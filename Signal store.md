Store создается через 
```
const initialState: BookStateInterface = {}
export const BookStore = signalStore(
	withState(initialStore)
);
```

Функция withState может принимать токен для инициализации состояния в момент создания стора;
```
withState(() => inject(SOME_TOKEN || SERVICE_TOKEN))
```
>Store можно провайдить глобально или использовать локально.
>Функция withComputed добавляет в состояние вычисляемые переменные. На вход принимает фабричную функцию, возвращающую объект.

>Функция withMethods  позволяет реализовать асинхронные операции (запросы, обновление состояния). 
>Для использования rxjs необходимо взаимодействовать с библиотекой rxjs interop.
https://ngrx.io/guide/signals/signal-store


```json
eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InVzZXJAZXhhbXBsZS5jb20iLCJnaXZlbl9uYW1lIjoiYWRnYWRzZ2FzZGciLCJuYmYiOjE3MjY5Mjg2MjAsImV4cCI6MTcyNzUzMzQyMCwiaWF0IjoxNzI2OTI4NjIwLCJpc3MiOiJodHRwOi8vbG9jYWxob3N0OjUyNDYiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjUyNDYifQ.WhuesbF6IhQqwsMiHsN_P5ed6TuWyeOCJK1w8ITgaPHfgyZJWbTRorreRCyayn9W5WtLN0MrCs6rb3wOz49IOA
```
```json
{
  "username": "adgadsgasdg",
  "email": "user@example.com",
  "password": "1231asfaasf1!"
}
```