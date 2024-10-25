

## Основа приложения на Python с REST API, Telegram ботом, OAuth2 и PostgreSQL

**Структура проекта:**

```
myapp/
├── app.py           # Основной файл приложения
├── api/
│   ├── __init__.py
│   ├── controllers/
│   │   ├── user_controller.py
│   │   └── ...
│   ├── middleware/
│   │   ├── auth_middleware.py
│   │   └── ...
│   ├── models/
│   │   ├── user.py
│   │   └── ...
│   ├── routes.py
│   └── db.py
├── telegram/
│   ├── __init__.py
│   ├── bot.py
│   └── ...
├── config.py       # Настройки приложения
├── requirements.txt  # Зависимости
└── ...

```

[**app.py](http://app.py/):**

```python
from flask import Flask
from flask_sqlalchemy import SQLAlchemy
from flask_oauthlib.provider import OAuth2Provider
from api.routes import api_bp
from telegram.bot import bot

app = Flask(__name__)
app.config.from_object('config')

db = SQLAlchemy(app)
oauth = OAuth2Provider(app)

# Регистрация Blueprints
app.register_blueprint(api_bp, url_prefix='/api')

# Запуск бота
bot.run_polling()

if __name__ == '__main__':
    app.run(debug=True)

```

[**config.py](http://config.py/):**

```python
SQLALCHEMY_DATABASE_URI = 'postgresql://user:password@host:port/database'
OAUTH2_CLIENT_ID = 'your_client_id'
OAUTH2_CLIENT_SECRET = 'your_client_secret'

```

[**db.py](http://db.py/):**

```python
from flask_sqlalchemy import SQLAlchemy

db = SQLAlchemy()

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(80), unique=True, nullable=False)
    # ... другие поля

def init_db():
    db.create_all()

```

**auth_middleware.py:**

```python
from functools import wraps

def requires_auth(f):
    @wraps(f)
    def decorated(*args, **kwargs):
        # Проверка наличия токена и его валидности
        # ...
        if not token_is_valid:
            return jsonify({'error': 'Unauthorized'}), 401
        return f(*args, **kwargs)
    return decorated

```

**user_controller.py:**

```python
from flask import request, jsonify
from api.middleware import requires_auth
from api.models import User

@api.route('/users', methods=['GET'])
@requires_auth
def get_users():
    # Получение пользователей из базы данных
    # ...
    return jsonify(users)

@api.route('/users/<int:user_id>', methods=['GET'])
@requires_auth
def get_user(user_id):
    # Получение пользователя по ID из базы данных
    # ...
    return jsonify(user)

```

[**bot.py](http://bot.py/):**

```python
from telegram import Update
from telegram.ext import Updater, CommandHandler, MessageHandler, filters

# ... обработчики команд и сообщений

def start(update: Update, context):
    # ...

def echo(update: Update, context):
    # ...

updater = Updater("YOUR_BOT_TOKEN", use_context=True)
dispatcher = updater.dispatcher

dispatcher.add_handler(CommandHandler("start", start))
dispatcher.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, echo))

updater.start_polling()
updater.idle()

```

**Примечания:**

- Замените `your_client_id`, `your_client_secret`, `user`, `password`, `host`, `port` и `database` на свои значения.
- Этот код является лишь основой. Вам нужно будет расширить его, добавив логику для обработки запросов, работы с базой данных, аутентификации и т.д.
- Для работы с Telegram ботом вам нужно будет получить токен от BotFather.
- Для OAuth2 вам нужно будет настроить OAuth2 provider.