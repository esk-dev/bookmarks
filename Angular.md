---
aliases:
  - Angular
---

### Вопросы на английском без ответов

- https://github.com/Yonet/Angular-Interview-Questions
- 

### Вопросы на английском с ответами

- https://github.com/sudheerj/angular-interview-questions

### Вопросы на русском

[https://github.com/Angular-RU/angular-ru-interview-questions](https://github.com/Angular-RU/angular-ru-interview-questions)

- **RxJS**
    - **What is RxJS?**
        
        RxJS - это библиотека для написания асинхронного кода и кода на основе коллбэков в функциональном реактивном стиле с использованием Observables. Многие API, такие как HttpClient, создают и потребляют наблюдаемые RxJS, а также используют операторы для обработки наблюдаемых.
        Например, вы можете импортировать наблюдаемые и операторы для использования HttpClient, как показано ниже.
        
        ```jsx
        import { Observable, throwError } from 'rxjs';
        import { catchError, retry } from 'rxjs/operators';
        ```
        
    - **What is subscribing?**
        
        An Observable instance begins publishing values only when someone subscribes to it. So you need to subscribe by calling the **subscribe()** method of the instance, passing an observer object to receive the notifications.
        
        Let's take an example of creating and subscribing to a simple observable, with an observer that logs the received message to the console.
        
        ```jsx
        Creates an observable sequence of 5 integers, starting from 1
        const source = range(1, 5);
        
        // Create observer object
        const myObserver = {
          next: x => console.log('Observer got a next value: ' + x),
          error: err => console.error('Observer got an error: ' + err),
          complete: () => console.log('Observer got a complete notification'),
        };
        
        // Execute with the observer object and Prints out each item
        source.subscribe(myObserver);
        // => Observer got a next value: 1
        // => Observer got a next value: 2
        // => Observer got a next value: 3
        // => Observer got a next value: 4
        // => Observer got a next value: 5
        // => Observer got a complete notification
        ```
        
    - **What is an observable?**
        
        An observable represents a sequence of values which can be observed.
        
    - **What is an observer?**
        
        Observer is an interface for a consumer of push-based notifications delivered by an Observable. It has below structure,
        
        ```jsx
        interface Observer<T> {
          closed?: boolean;
          next: (value: T) => void;
          error: (err: any) => void;
          complete: () => void;
        }
        ```
        
        A handler that implements the Observer interface for receiving observable notifications will be passed as a parameter for observable as below,
        
        ```jsx
        myObservable.subscribe(myObserver);
        ```
        
        **Note:** If you don't supply a handler for a notification type, the observer ignores notifications of that type.
        
    - **What is the difference between promise and observable?**
        
        Below are the list of differences between promise and observable,
        
        | Observable | Promise |
        | --- | --- |
        | Declarative: Computation does not start until subscription so that they can be run whenever you need the result | Execute immediately on creation |
        | Provide multiple values over time | Provide only one |
        | Subscribe method is used for error handling which makes centralized and predictable error handling | Push errors to the child promises |
        | Provides chaining and subscription to handle complex applications | Uses only .then() clause |
    - **How do you perform error handling in observables?**
        
        You can handle errors by specifying an **error callback** on the observer instead of relying on try/catch which are ineffective in asynchronous environment.
        
        For example, you can define error callback as below,
        
        ```jsx
        myObservable.subscribe({
          next(num) { console.log('Next num: ' + num)},
          error(err) { console.log('Received an errror: ' + err)}
        });
        ```
        
    - **What are the utility functions provided by RxJS?**
        
        Библиотека RxJS также предоставляет приведенные ниже служебные функции для создания наблюдаемых объектов и работы с ними.
        1. Преобразование существующего кода для асинхронных операций в наблюдаемые объекты
        2. Перебор значений в потоке
        3. Сопоставление значений различным типам
        4. Фильтрация потоков
        5. Составление нескольких потоков
        
- **Что такое Angular?**
    
    **Angular**— это платформа для разработки мобильных и десктопных веб-приложений. Наши приложения теперь представляют из себя «толстый клиент», где управление отображением и часть логики перенесены на сторону браузера. Так сервер уделяет больше времени доставке данных, плюс пропадает необходимость в постоянной перерисовке. С Angular мы описываем структуру приложения декларативно, а с TypeScript начинаем допускать меньше ошибок, благодаря статической типизации. В Angular присутствует огромное количество возможностей из коробки. Это может быть одновременно и хорошо и плохо, в зависимости от того, что вам необходимо.
    
    **Какие плюсы можно выделить**:
    
    - Поддержка Google, Microsoft
    - Инструменты разработчика (CLI)
    - Typescript из коробки
    - Реактивное программирование с RxJS
    - Единственный фреймворк с Dependency Injection из коробки
    - Шаблоны, основанные на расширении HTML
    - Кроссбраузерный Shadow DOM из коробки (либо его эмуляция)
    - Кроссбраузерная поддержка HTTP, WebSockets, Service Workers
    - Не нужно ничего дополнительно настраивать. Больше никаких оберток. jQuery плагины и D3 можно использовать на прямую
    - Более современный фреймворк, чем AngularJS (на уровне React, Vue)
    - Большое комьюнити
    
    **Минусы**:
    
    - Выше порог вхождения из-за Observable (RxJS) и Dependency Injection
    - Чтобы все работало хорошо и быстро нужно тратить время на дополнительные оптимизации (он не супер быстрый, по умолчанию, но быстрее AngularJS во много раз)
    - Если вы планируете разрабатывать большое enterprise-приложение, то в этом случае, у вас нет архитектуры из коробки - нужно добавлять Mobx, Redux, MVVM, CQRS/CQS или другой state-менеджер, чтобы потом не сломать себе мозг
    - Angular-Universal имеет много подводных камней
    - Динамическое создание компонентов оказывается нетривиальной задачей
- **Какой должна быть структура каталогов компонентов любого Angular приложения и почему?**
    
    The main building blocks of an Angular application are shown in the diagram below: 
    
    ![Untitled](Angular%20a6c40ddcb5f4467482b44ea8b079dc03/Untitled.png)
    
- **What are the key components of Angular?**
    
    Angular has the key components below
    
    1. **Component:** These are the basic building blocks of an Angular application to control HTML views.
    2. **Modules:** An Angular module is a set of angular basic building blocks like components, directives, services etc. An application is divided into logical pieces and each piece of code is called as "module" which perform a single task.
    3. **Templates:** These represent the views of an Angular application.
    4. **Services:** Are used to create components which can be shared across the entire application.
    5. **Metadata:** This can be used to add more data to an Angular class.
- **What are components?**
    
    Components are the most basic UI building block of an Angular app, which form a tree of Angular components. These components are a subset of directives. Unlike directives, components always have a template, and only one component can be instantiated per element in a template. Let's see a simple example of Angular component
    
- **Что такое MVVM и в чем разница перед MVC?**
    
    **MVVM** - шаблон проектирования архитектуры приложения. Состоит из 3 ключевых блоков: Model, View, ViewModel.
    
    Отличие от MVС заключаются в:
    
    - View реагирует на действия пользователя и передает их во View Model через Data Binding.
    - View Model, в отличие от контроллера в MVC, имеет особый механизм, автоматизирующий связь между View и связанными свойствами в ViewModel.
    
    Привязка данных между View и ViewModel может быть односторонней или двусторонней (one-way, two-way data-binding).
    
- **Расскажите об основных параметрах @NgModule, @Component, @Directive, @Injectable, @Pipe**
    
    Декораторы динамически подключают дополнительное поведение к объекту. Они помечают класс и предоставляют конфигурационные метаданные.
    
    ### @NgModule может содержать следующие параметры:
    
    - providers - список инжектируемых объектов, которые добавляются в этот модуль
    - declarations - компоненты, директивы и пайпы, принадлежащие этому модулю
    - imports - модули, которые экспортируются декларируемыми и доступны в шаблоне этого модуля
    - exports - компоненты, директивы и пайпы, которые объявлены декларируемыми, и могут быть им пользованы в шаблоне любого компонента, которые принадлежит NgModule импортирующему их.
    - entryComponent - компилируемые компоненты при определении NgModule, для динамической загрузки в view.
    - bootstrap - компоненты, которые загружаются при загрузке этого модуля, автоматически добавляются в entryComponent.
    - schemas - набор схем, объявляющих разрешенные элементы в MgModules
    - id - имя или путь, уникальный идентификатор этого NgModule в getModuleFactory. Если не заполнять - не будет там зарегистрирован.
    - jit - если true, то этот модуль будет пропущен компилятором AOT и всегда будет компилироваться JIT.
    
    ### @Component может содержать следующие параметры:
    
    - changeDetection - стратегия обнаружения изменений, используемая для этого компонента
    - viewProviders - инжектируемые объекты, которые видны DOM children этого компонента.
    - moduleId - id модуля, к которому относится компонент.
    - templateUrl - относительный путь или абсолютный URL к шаблону компонента.
    - template - инлайн шаблон для этого компонента.
    - styleUrls - один и более путь до файла, содержащего CSS, абсолютный или относительный.
    - styles - инлайн CSS, используемые в этом компоненте.
    - animations - один и более вызовов анимации trigger(), содержащих state() и transition().
    - encapsulation - правила инкапсуляции для шаблона и CSS.
    - interpolation - переопределение базовых знаков интерполяции.
    - entryComponents - компоненты, которые должны быть скомпилированы вместе с этим компонентом. Для каждого упомянутого здесь компонента создается ComponentFactory и сохраняется в ComponentFactoryResolver.
    - preserveWhitespaces - при значении true удаляются потенциально лишние пробелы из скомпилированного шаблона.
    
    ### @Directive может содержать следующие параметры:
    
    - selector - CSS-селектор, который идентифицирует эту директиву в шаблоне и запускает создание этой директивы.
    - inputs - свойство для определения значение @Input() параметра. Значение из inputs можно сразу использовать в шаблоне, без объявления переменной в классе. Пример объявления: inputs: ['name', 'id: id-from-parent']. Значение в inputs массиве может состоять из:Пример использования:
        - directiveProperty - наименование свойства @Input, которое будет использоваться в дочернем компоненте для вывода в шаблоне и использования в самом классе.
        - bindingProperty - наименование свойства, из которого будет производится чтение и запись в directiveProperty. Не обязательное. При отсутсвии параметра значение будет браться из directiveProperty
        
        ```jsx
        @Component({
          selector: "child-component",
          template: `Name {{ name }} Id {{ id }}`,
          inputs: ["name", "id: parentId"],
        })
        export class ChildComponent {}
        
        @Component({
          selector: "parent-component",
          template: `
            <child-component
              [name]="parentName"
              [parentId]="parentIdValue"
            ></child-component>
          `,
        })
        export class Parent {
          public parentIdValue = "123";
          public parentName = "Name";
        }
        ```
        
    - outputs - свойство для определения @Output. В отличии от inputs, объявление свойства в классе обязательно. Пример:
        
        ```jsx
        @Component({
          selector: "child-dir",
          outputs: ["bankNameChange"],
          template: `<input (input)="bankNameChange.emit($event.target.value)" />`,
        })
        class ChildDir {
          bankNameChange: EventEmitter<string> = new EventEmitter<string>();
        }
        
        @Component({
          selector: "main",
          template: `
            {{ bankName }}
            <child-dir (bankNameChange)="onBankNameChange($event)"></child-dir>
          `,
        })
        class MainComponent {
          bankName: string;
        
          onBankNameChange(bankName: string) {
            this.bankName = bankName;
          }
        }
        ```
        
    - providers - настраивает инжектор этой директивы или компонента с помощью токена.
    - exportAs - определяет имя, которое можно использовать в шаблоне для присвоения этой директивы переменной.
    - queries - настраивает запросы, которые могут быть инжектированы в директиву.
    - host - составляет свойства класса со сбайнженными элементами для свойств, атрибутов и ивентов.
    - jit - если true, то этот модуль будет пропущен компилятором AOT и всегда будет компилироваться JIT.
    
    ### @Injectable может содержать следующие параметры:
    
    - providedIn - определяет, где будет заинжектировано, либо, если объявлено "root" распространится на все приложение.
    
    ### @Pipe может содержать следующие параметры:
    
    - name - имя пайпа, которое будет использовано в шаблоне.
    - pure - если true, то пайп считается "чистым", и метод transform() вызовется только при изменении его входных агрументов. По умолчанию стоит true.
- **What is a module?**
    
    Модули являются логическими границами в вашем приложении, и приложение разделено на отдельные модули для разделения функциональности вашего приложения. Давайте рассмотрим пример корневого модуля app.module.ts, объявленного с помощью декоратора @NgModule, как показано ниже:
    
    ```jsx
    import { NgModule }      from '@angular/core';
    import { BrowserModule } from '@angular/platform-browser';
    import { AppComponent }  from './app.component';
    
    @NgModule ({
       imports:      [ BrowserModule ],
       declarations: [ AppComponent ],
       bootstrap:    [ AppComponent ],
       providers: []
    })
    export class AppModule { }
    ```
    
    The NgModule decorator has five important(among all) options
    
    1. The imports option is used to import other dependent modules. The BrowserModule is required by default for any web based angular application
    2. The declarations option is used to define components in the respective module
    3. The bootstrap option tells Angular which Component to bootstrap in the application
    4. The providers option is used to configure set of injectable objects that are available in the injector of this module.
    5. The entryComponents option is a set of components dynamically loaded into the view.
- **Angular Template синтаксис**
    - **What is a template?**
        
        A template is a HTML view where you can display data by binding controls to properties of an Angular component. You can store your component's template in one of two places. You can define it inline using the template property, or you can define the template in a separate HTML file and link to it in the component metadata using the @Component decorator's templateUrl property.
        
    - **What is a data binding?**
        
        Data binding is a core concept in Angular and allows to define communication between a component and the DOM, making it very easy to define interactive applications without worrying about pushing and pulling data. There are four forms of data binding(divided as 3 categories) which differ in the way the data is flowing.
        
        1. **From the Component to the DOM:**
            
            **Interpolation:** {{ value }}: Adds the value of a property from the component
            
            ```html
            <li>Name: {{ user.name }}</li>
            <li>Address: {{ user.address }}</li>
            ```
            
            **Property binding:** [property]=”value”: The value is passed from the component to the specified property or simple HTML attribute
            
            ```jsx
            <input type="email" [value]="user.email">
            ```
            
        2. **From the DOM to the Component:** **Event binding: (event)=”function”:** When a specific DOM event happens (eg.: click, change, keyup), call the specified method in the component
            
            ```jsx
            <button (click)="logout()"></button>
            ```
            
        3. **Two-way binding:** **Two-way data binding:** [(ngModel)]=”value”: Two-way data binding allows to have the data flow both ways. For example, in the below code snippet, both the email DOM input and component email property are in sync
            
            ```jsx
            <input type="email" [(ngModel)]="user.email">
            ```
            
        
        **How do you categorize data binding types?**
        
        Binding types can be grouped into three categories distinguished by the direction of data flow. They are listed as below,
        
        1. From the source-to-view
        2. From view-to-source
        3. View-to-source-to-view
        
        The possible binding syntax can be tabularized as below,
        
        | Data direction | Syntax | Type |
        | --- | --- | --- |
        | From the source-to-view(One-way) | 1. {{expression}} 2. [target]="expression" 3. bind-target="expression" | Interpolation, Property, Attribute, Class, Style |
        | From view-to-source(One-way) | 1. (target)="statement" 2. on-target="statement" | Event |
        | View-to-source-to-view(Two-way) | 1. [(target)]="expression" 2. bindon-target="expression" | Two-way |
    - **Что такое интерполяция в Angular?**
        
        Разметка интерполяции с внедренными выражениями используется в Angular для присвоения данных текстовым нодам и значения аттрибутов.
        
    - **Что такое директива и как создать собственную?**
        
        Директивы бывают трех видов: компонент, структурные и атрибутные (см. выше).
        
        ### Создание атрибутных директив:
        
        Декоратор определяет селектор атрибута [appHighlight], [] - указывают что это селектор атрибута. Angular найдет каждый элемент в шаблоне с этим атрибутом и применит к ним логику директивы.
        
        ```jsx
        @Directive({
          selector: "[appHighlight]",
        })
        export class HighlightDirective {
          constructor(el: ElementRef) {
            el.nativeElement.style.backgroundColor = "yellow";
          }
        }
        ```
        
        Необходимо указать в конструкторе ElementRef, чтобы через его свойство nativeElement иметь прямой доступ к DOM элементу, который должен быть изменен. Теперь, используя @HostListener, можно добавить обработчики событий, взаимодействующие с декоратором.
        
        ```jsx
        @Component()
        class EtcComponent {
          @HostListener("mouseenter")
          public onMouseEnter(): void {
            this.highlight("yellow");
          }
        
          @HostListener("mouseleave")
          public onMouseLeave(): void {
            this.highlight(null);
          }
        
          private highlight(color: string): void {
            this.el.nativeElement.style.backgroundColor = color;
          }
        }
        ```
        
        ### Структурные директивы создаются так:
        
        Напишем UnlessDirective, которая будет противоположна NgIf.Необходимо использовать @Directive, и импортировать Input, TemplateRef, и ViewContainerRef. Они вам понадобятся при воздании любой структурной директивы.
        
        ```jsx
        import { Directive, Input, TemplateRef, ViewContainerRef } from "@angular/core";
        
        @Directive({ selector: "[appUnless]" })
        export class UnlessDirective {}
        ```
        
        В конструкторе мы получаем доступ к view container и содержимое .
        
        ```jsx
          constructor(
            private templateRef: TemplateRef<any>,
            private viewContainer: ViewContainerRef) { }
        ```
        
        Наша директива предполагает работу с true/false. Для этого нужно свойство appUnless, добавленное через @Input.
        
        ```jsx
        @Directive({ selector: "[appUnless]" })
        export class UnlessDirective {
          @Input() public set appUnless(condition: boolean) {
            if (!condition && !this.hasView) {
              this.viewContainer.createEmbeddedView(this.templateRef);
              this.hasView = true;
            } else if (condition && this.hasView) {
              this.viewContainer.clear();
              this.hasView = false;
            }
          }
        }
        ```
        
    - **В чем разница между структурной и атрибутной директивой, назовите встроенные директивы?**
        - Структурные директивы влияют на DOM и могут добавлять/удалять элементы(ng-template, NgIf, NgFor, NgSwitch, etc)
        - Атрибутные директивы меняют внешний вид или поведение элементов, компонентов или других директив(NgStyle, NgClass, etc).
    - **Для чего нужны директивы ng-template, ng-container, ng-content?**
        
        ### 1. ng-template
        
        `<template>` — это механизм для отложенного рендера клиентского контента, который не отображается во время загрузки, но может быть инициализирован при помощи JavaScript.Template можно представить себе как фрагмент контента, сохранённый для последующего использования в документе. Хотя парсер и обрабатывает содержимое элемента `template` во время загрузки страницы, он делает это только чтобы убедиться в валидности содержимого; само содержимое при этом не отображается.
        
        `<ng-template>` - является имплементацией стандартного элемента template, данный элемент появился с четвертой версии Angular, это было сделано с точки зрения совместимости со встраиваемыми на страницу template элементами, которые могли попасть в шаблон ваших компонентов по тем или иным причинам.
        
        Пример:
        
        ```html
        <div class="lessons-list" *ngIf="lessons else loading">...</div>
        
        <ng-template #loading>
          <div>Loading...</div>
        </ng-template>
        ```
        
        ### 2. ng-container
        
        `<ng-container>` - это логический контейнер, который может использоваться для группировки узлов, но не отображается в дереве DOM как узел (node).
        
        На самом деле структурные директивы (*ngIf, *ngFor, …) являются синтаксическим сахаром для наших шаблонов. В реальности, данные шаблоны трансформируются в такие конструкции:
        
        ```html
        <ng-template [ngIf]="lessons" [ngIfElse]="loading">
           <div class="lessons-list">
             ...
           </div>
        </div>
        
        <ng-template #loading>
            <div>Loading...</div>
        </ng-template>
        ```
        
        Но что делать, если я хочу применить несколько структурных директив? (спойлер: к сожалению, так нельзя сделать)
        
        ```html
        <div class="lesson" *ngIf="lessons" *ngFor="let lesson of lessons">
          <div class="lesson-detail">{{lesson | json}}</div>
        </div>
        ```
        
        ```html
        Uncaught Error: Template parse errors:
        Can't have multiple template bindings on one element. Use only one attribute
        named 'template' or prefixed with *
        ```
        
        Но можно сделать так:
        
        ```html
        <div *ngIf="lessons">
          <div class="lesson" *ngFor="let lesson of lessons">
            <div class="lesson-detail">{{lesson | json}}</div>
          </div>
        </div>
        ```
        
        Однако, чтобы избежать необходимости создавать дополнительный div, мы можем вместо этого использовать директиву ng-container:
        
        ```html
        <ng-container *ngIf="lessons">
          <div class="lesson" *ngFor="let lesson of lessons">
            <div class="lesson-detail">{{lesson | json}}</div>
          </div>
        </ng-container>
        ```
        
        Как мы видим, директива ng-container предоставляет нам элемент, в котором мы можем использовать структурную директиву, без необходимости создавать дополнительный элемент.
        
        Еще пара примечательных примеров, если все же вы хотите использовать ng-template вместо ng-container, по определенным правилам вы не сможете использовать полную конструкцию структурных директив.
        
        Вы можете писать либо так:
        
        ```html
        <div class="mainWrap">
          <ng-container *ngIf="true">
            <h2>Title</h2>
            <div>Content</div>
          </ng-container>
        </div>
        ```
        
        Либо так:
        
        ```html
        <div class="mainWrap">
          <ng-template [ngIf]="true">
            <h2>Title</h2>
            <div>Content</div>
          </ng-template>
        </div>
        ```
        
        На выходе, при рендеринге будет одно и тоже:
        
        ```html
        <div class="mainWrap">
          <h2>Title</h2>
          <div>Content</div>
        </div>
        ```
        
        ### 3. ng-content
        
        `<ng-content>` - позволяет внедрять родительским компонентам html-код в дочерние компоненты.
        
        Здесь на самом деле, немного сложнее уже чем с ng-template, ng-container. Так как ng-content решает задачу проецирования контента в ваши веб-компоненты. Веб-компоненты состоят из нескольких отдельных технологий. Вы можете думать о Веб-компонентах как о переиспользуемых виджетах пользовательского интерфейса, которые создаются с помощью открытых веб-технологий. Они являются частью браузера и поэтому не нуждаются во внешних библиотеках, таких как jQuery или Dojo. Существующий Веб-компонент может быть использован без написания кода, просто путем импорта выражения на HTML-страницу. Веб-компоненты используют новые или разрабатываемые стандартные возможности браузера.
        
        Давайте представим ситуацию от обратного, нам нужно параметризовать наш компонент. Мы хотим сделать так, чтобы на вход в компонент мы могли передать какие-либо статичные данные. Это можно сделать несколькими способами.
        
        comment.component.ts:
        
        ```html
        @Component({
          selector: "comment",
          template: `
            <h1>Комментарий:</h1>
            <p>{{ data }}</p>
          `,
        })
        export class CommentComponent {
          @Input() data: string = null;
        }
        ```
        
        app.component.html
        
        ```html
        <div *ngFor="let message of comments">
          <comment [data]="message"></comment>
        </div>
        ```
        
        Но можно поступить и другим путем.comment.component.ts:
        
        ```html
        @Component({
          selector: "comment",
          template: `
            <h1>Комментарий:</h1>
            <ng-content></ng-content>
          `,
        })
        export class CommentComponent {}
        ```
        
        app.component.html
        
        ```html
        <div *ngFor="let message of comments">
          <comment>
            <p>{{message}}</p>
          </comment>
        </div>
        ```
        
        Конечно, эти примеры плохо демонстрируют подводные камни, свои плюсы и минусы. Но второй способ демонстрирует подход при работе, когда мы оперируем независимыми абстракциями и можем проецировать контент внутрь наших компонентов (подход веб-компонентов).
        
    - **What are the differences between Component and Directive?**
    - **What are pipes?**
        
        Пайп принимает данные в качестве входных данных и преобразует их в желаемый результат. Например, давайте возьмем пайп, чтобы преобразовать свойство дня рождения компонента в удобную для человека дату с помощью конвейера даты.
        
        ```jsx
        import { Component } from '@angular/core';
        
        @Component({
          selector: 'app-birthday',
          template: `<p>Birthday is {{ birthday | date }}</p>`
        })
        export class BirthdayComponent {
          birthday = new Date(1987, 6, 18); // June 18, 1987
        }
        ```
        
    - **What is a parameterized pipe?**
        
        Пайп может принимать любое количество необязательных параметров для точной настройки вывода. Параметризованный пайп можно создать, объявив имя пайпа с двоеточием ( : ), а затем значение параметра. Если канал принимает несколько параметров, разделяйте значения двоеточиями. Возьмем пример дня рождения в определенном формате (дд/мм/гггг):
        
        ```jsx
        import { Component } from '@angular/core';
        
            @Component({
              selector: 'app-birthday',
              template: `<p>Birthday is {{ birthday | date:'dd/MM/yyyy'}}</p>` // 18/06/1987
            })
            export class BirthdayComponent {
              birthday = new Date(1987, 6, 18);
            }
        ```
        
        **Note:** The parameter value can be any valid template expression, such as a string literal or a component property.
        
    - **What is the difference between pure and impure pipe?**
        
        Чистый пайп вызывается только тогда, когда Angular обнаруживает изменение значения или параметров, переданных в канал. Например, любые изменения примитивного входного значения (строка, число, логическое значение, символ) или измененная ссылка на объект (дата, массив, функция, объект). Нечистый пайп вызывается для каждого цикла обнаружения изменений независимо от того, изменяются ли значение или параметры. т. е. нечистый пайп вызывается так же часто, как и каждое нажатие клавиши или движение мыши.
        
- **Angular Render and Core**
    - **Каков жизненный цикл у компонентов?**
        
        После создания компонента или директивы через вызов конструктора, Angular вызывает методы жизненного цикла в следующей последовательности в строго определенные моменты:
        
        - ngOnChanges() - вызывается когда Angular переприсваивает привязанные данные к input properties. Метод получает объект SimpleChanges, со старыми и новыми значениями. Вызывается перед NgOnInit и каждый раз, когда изменяется одно или несколько связанных свойств.
        - ngOnInit() - инициализирует директиву/компонент после того, как Angular впервые отобразит связанные свойства и устанавливает входящие параметры.
        - ngDoCheck() - при обнаружении изменений, которые Angular не может самостоятельно обнаружить, реагирует на них.
        - ngAfterContentInit() - вызывается после того, как Angular спроецирует внешний контент в отображение компонента или отображение с директивой. Вызывается единожды, после первого ngDoCheck().
        - ngAfterContentChecked() - реагирует на проверку Angular-ом проецируемого содержимого. Вызывается после ngAfterContentInit() и каждый последующий ngDoCheck().
        - ngAfterViewInit() - вызывается после инициализации отображения компонента и дочерних/директив. Вызывается единожды, после первого ngAfterContentChecked().
        - ngAfterViewChecked() - реагирует на проверку отображения компонента и дочерних/директив. Вызывается после ngAfterViewInit() и каждый последующий ngAfterContentChecked().
        - ngOnDestroy() - после уничтожения директивы/компонента выполняется очистка. Отписывает Observables и отключает обработчики событий, чтобы избежать утечек памяти.
        
        **Основное отличие constructor от ngOnInit?**
        
        Конструктор сам по себе является фичей самого класса, а не Angular. Основная разница в том, что Angular запустит `ngOnInit`, после того, как закончит настройку компонента, то есть, это сигнал, благодаря которому свойства `@Input()`и другие байндинги, и декорируемые свойства доступны в `ngOnInit`, но не определены внутри конструктора, по дизайну.
        
    - **Объясните механизм загрузки (bootstrap) Angular-приложения в браузере?**
        
        Запуск Angular приложения начинается с файла **main.ts**. Этот файл содержит в себе примерно следующее:
        
        `import { platformBrowserDynamic } from "@angular/platform-browser-dynamic";
        import { AppModule } from "./app/app.module";
        
        const platform = platformBrowserDynamic();
        
        platform.bootstrapModule(AppModule);`
        
        platformBrowserDynamic запускает AppModule. После этого, начинает работать логика в AppModule.
        
        В AppModule обычно задается компонент, который будет использоваться для отображения при загрузке. Компонент находится в параметре **bootstrap**
        
        `@NgModule({
          imports: [BrowserModule, FormsModule],
          declarations: [AppComponent],
          bootstrap: [AppComponent],
        })
        export class AppModule {}`
        
    - **Как происходит взаимодействие компонентов в Angular (опишите components view)?**
        
        Взаимодействие компонентов может быть:
        
        - **между родительским и дочерним компонентом** - селектор одного компонента объявлен в шаблоне другого
        - **между компонентами одного уровня** - селекторы компонентов не вложенные
        
        ### Способы взаимодействия
        
        1. **@Input()/@Output() декораторы свойств** - используются между дочерним и родительским компонентами. В @Input() можно получить значение из родителя. Через @Output() отправить данные из дочернего в родительский компонент.
            
            В шаблоне родительского компонента ставится селектор дочернего. В селекторе дочернего компонента прописываются атрибуты, через которые будут передаваться данные в переменные @Input()/@Output(). Для обозначения @Input свойства в селекторе нужно прописать . Для обозначения @Output свойства в селекторе нужно прописать .
            
            В классе родительского компонента нужно обозначить public свойства/методы, которые будут прописаны в атрибутах дочернего селектора.
            
            В классе дочернего компонента нужно прописать public свойства с декораторами @Input()/@Output(). Названия свойств должны совпадать с именами в атрибутах дочернего селектора. В @Input() можно передать значения как обычных типов данных (string, number, Array и тп), так и потоки (Subject, Observable). В @Output обычно используется EventEmitter. Через него можно отправить значения в функцию родительского компонента, которая прописана в атрибуте селектора.
            
            Пример
            
            `@Component({
              selector: "parent",
              template: `
                <div>
                  <child [count]="value" (increment)="onInstement($event)"></child>
                </div>
              `,
            })
            export class ParentComponent {
              public value: number = 0;
            
              public onIncrement(value: number): void {
                // actions with child's value
              }
            }
            
            @Component({
              selector: "child",
              template: `
                <div>
                  <button type="button" (click)="onClickIncrement()">+1</button>
                </div>
              `,
              changeDetection: ChangeDetectionStrategy.OnPush, //см пункт "Какие существуют стратегии обнаружения изменений?"
            })
            export class ChildComponent {
              @Input() public count: number;
            
              @Output() public increment: EventEmitter<number> = new EventEmitter();
            
              public onClickIncrement(): void {
                const result = this.count++;
                this.increment.emit(result);
              }
            }`
            
        2. **@ViewChild() директива** - получение доступа к свойствам дочернего компонента. В родительском шаблоне нужно указать селектор дочернего. Так же, в родительском компоненте нужно обозначить public свойство с директивой @ViewChild().
            
            По умолчанию, доступ к свойствам @ViewChild() можно получить в хуке ngAfterViewInit(). Так же, нужно учитывать свойство **static** при использовании @ViewChild(). **static** параметр указывает, когда можно получить доступ к ViewChild() - до или после change detection. Это может понадобится, когда @ViewChild используется в циклах (*ngFor) или доступен только по условию (*ngIf). Если static = false, то доступ можно получить до change detection в хуке ngAfterViewInit().
            
            Примеры
            
            `@Component({
              selector: "parent",
              template: `<child #childRef *ngIf="isShowChild"></child>`,
            })
            export class ParentComponent {
              @ViewChild("childRef", { static: false }) public viewChild: ChildComponent;
            
              public isShowChild: boolean = false;
            
              public ngAfterViewInit(): void {
                console.log(this.viewChild.title);
              }
            }
            
            @Component({
              selector: "parent",
              template: `<child #childRef></child>`,
            })
            export class ParentComponent {
              @ViewChild("childRef", { static: false }) public viewChild: ChildComponent;
            
              public ngAfterViewInit(): void {
                console.log(this.viewChild.title);
              }
            }`
            
        3. **Через сервис** - передача данных между компонентами через единый сервис. Этим способом можно взаимодействовать с компонентами одного уровня. Так же, можно избавиться от иерархии зависимостей и не использовать всплывающие события (Output)
            
            Необходимо создать общий сервис, который объявляется в параметре providers в общем модуле соединяемых компонентов. В сервисе можно создать public свойства и методы для передачи данных. Можно использовать Observable и Subjects для передачи данных. Пример:
            
            `@Injectable()
            export class CountService {
              private count$: BehaviorSubject<number> = new BehaviorSubject(0);
            
              public get value$(): Observable<number> {
                return this.count$.asObservable();
              }
            
              public get value(): number {
                return this.count$.getValue();
              }
            
              public setState(value: number): void {
                this.count$.next(value);
              }
            
              public reset(): void {
                this.count$.next(0);
              }
            }
            
            @Component({
              selector: "counter",
              template: `
                 value = {{ counter.value$ | async }}  <br/>
                <button type='button' (click)='counter.setState(counter.value + 1)>+1</button>
                <button type='button' (click)='counter.setState(counter.value - 1)>-1</button>
                <button type='reset' (click)='counter.reset()>reset</button>
              `,
            })
            export class CounterComponent {
              constructor(private counter: CountService) {}
            }`
            
    - **Что такое Shadow DOM и как с ним работать в Angular?**
    - **В чем преимущества и недостатки Regular DOM (Angular) перед Virtual DOM (React)?**
    - **What is dependency injection in Angular?**
        
        Dependency injection (DI), is an important application design pattern in which a class asks for dependencies from external sources rather than creating them itself. Angular comes with its own dependency injection framework for resolving dependencies( services or objects that a class needs to perform its function).So you can have your services depend on other services throughout your application.
        
        Ссылки по теме
        
        [Angular Dependency Injection: Complete Guide](https://blog.angular-university.io/angular-dependency-injection/)
        
        [Angular: полное руководство для "Внедрения зависимостей"](https://habr.com/ru/company/rshb/blog/586874/)
        
    - **Что такое ngZone?**
        
        [NgZone](https://angular.io/api/core/NgZone) - это сервис, который является обёрткой над zone.js, для выполнения кода внутри или вне зоны Angular. Этот сервис создаёт зону с именем angular для автоматического запуска обнаружения изменений, когда выполняются следующие условия:
        
        - Когда выполняется синхронная или асинхронная функция
        - Когда нет запланированной микро-задачи в очереди
        
        Наиболее распространённое применение NgZone — это оптимизация производительности посредством выполнения асинхронной логики вне зоны Angular (метод `runOutsideAngular`), тем самым не вызывая обнаружение изменений или обработку ошибок. Или наоборот, данный сервис может использоваться для выполнения логики внутри зоны (метод `run`), что в конечном итоге приведёт к тому, что Angular снова вызовет обнаружение изменений и при необходимости перерисует представление.
        
    - 
- **Angular with Backend integrations**
    - **What is HttpClient and its benefits?**
        
        Most of the Front-end applications communicate with backend services over HTTP protocol using either XMLHttpRequest interface or the fetch() API. Angular provides a simplified client HTTP API known as **HttpClient** which is based on top of XMLHttpRequest interface. This client is avaialble from `@angular/common/http` package. You can import in your root module as below,
        
        `import { HttpClientModule } from '@angular/common/http';`
        
        The major advantages of HttpClient can be listed as below,
        
        1. Contains testability features
        2. Provides typed request and response objects
        3. Intercept request and response
        4. Supports Observalbe APIs
        5. Supports streamlined error handling
    - **Explain on how to use HttpClient with an example?**
        1. Below are the steps need to be followed for the usage of HttpClient.Since the above service method returns an Observable which needs to be subscribed in the component.
            1. Import HttpClient into root module:
                
                `import { HttpClientModule } from '@angular/common/http';
                @NgModule({
                  imports: [
                    BrowserModule,
                    // import HttpClientModule after BrowserModule.
                    HttpClientModule,
                  ],
                  ......
                  })
                 export class AppModule {}`
                
            2. Inject the HttpClient into the application: Let's create a userProfileService(userprofile.service.ts) as an example. It also defines get method of HttpClient
                
                `import { Injectable } from '@angular/core';
                import { HttpClient } from '@angular/common/http';
                
                const userProfileUrl: string = 'assets/data/profile.json';
                
                @Injectable()
                export class UserProfileService {
                  constructor(private http: HttpClient) { }
                
                  getUserProfile() {
                    return this.http.get(this.userProfileUrl);
                  }
                }`
                
            3. Create a component for subscribing service: Let's create a component called UserProfileComponent(userprofile.component.ts) which inject UserProfileService and invokes the service method,
                
                `fetchUserProfile() {
                  this.userProfileService.getUserProfile()
                    .subscribe((data: User) => this.user = {
                        id: data['userId'],
                        name: data['firstName'],
                        city:  data['city']
                    });
                }`
                
        2. How can you read full response?
            
            The response body doesn't may not return full response data because sometimes servers also return special headers or status code which are important for the application workflow. Inorder to get full response, you should use observe option from HttpClient,
            
            `getUserResponse(): Observable<HttpResponse<User>> {
              return this.http.get<User>(
                this.userUrl, { observe: 'response' });
            }`
            
            Now HttpClient.get() method returns an Observable of typed HttpResponse rather than just the JSON data.
            
    - **Какими способами можно взаимодействовать с API бэкенда, что требуется для проксирования запросов?**
        
        **Взаимодействие с API**
        
        В экосистеме ангуляр существует пакет для общения с сервером (@angular/common/http), которого достаточно для повседневной разработки. Его интерфейс основан на rxjs потоках, поэтому его легко использовать для работы с потоками данных в приложении.
        
        Кроме этого, как и в ванильной версии javascript, можно использовать XMLHttpRequest, fetch API, axios(или многие другие библиотеки), но их использование вместо встроенного клиента, считается неоправданным и всячески возбраняется.
        
        Существуют и другие способы взаимодействия с сервером(см. Веб-сокеты), но для них не существует каноничных встроенных библиотек, поэтому используются сторонние библиотеки или собственные реалиации. Хорошей практикой здесь будет привести интерфейс построенный на промисах и обратных вызовах(callback) к интерфейсу основанному на rxjs потоках, для естественного использования в экосистеме Angular.
        
        **Proxy**
        
        Чтобы тестировать взаимодействие приложения с сервером, который должен находиться на том же домене, используется [функциональность в Angular CLI](https://angular.io/guide/build#proxying-to-a-backend-server) для этого нужно создать файл с конфигурацией прокси, где будут указаны:
        
        - Контекст для проксирования
        - Ссылка на работающий экземпляр API
        - secure: false для работы в тестовой среде без сертификатов
        
        Также большинство серверов не настроены для работы с разными доменами([CORS](https://developer.mozilla.org/ru/docs/Web/HTTP/CORS)), поэтому для корректной работы на API сервере, необходимо явно указать с какого домена(ов) можно принимать запросы.
        
    - **Что такое HTTP Interceptors?**
        
        Interceptor (перехватчик) - просто причудливое слово для функции, которая получает запросы / ответы до того, как они будут обработаны / отправлены на сервер. Нужно использовать перехватчики, если имеет смысл предварительно обрабатывать многие типы запросов одним способом. Например нужно для всех запросов устанавливать хедер авторизации `Bearer`:
        
        token.interceptor.ts
        
        `import { Injectable } from "@angular/core";
        import {
          HttpInterceptor,
          HttpRequest,
          HttpHandler,
          HttpEvent,
        } from "@angular/common/http";
        import { Observable } from "rxjs/Observable";
        
        @Injectable()
        export class TokenInterceptor implements HttpInterceptor {
          public intercept(
            req: HttpRequest<any>,
            next: HttpHandler
          ): Observable<HttpEvent<any>> {
            const token = localStorage.getItem("token") as string;
        
            if (token) {
              req = req.clone({
                setHeaders: {
                  Authorization: `Bearer ${token}`,
                },
              });
            }
        
            return next.handle(req);
          }
        }`
        
        И регистрируем перехватчик как синглтон в провайдерах модуля:
        
        app.module.ts
        
        `import { NgModule } from "@angular/core";
        import { BrowserModule } from "@angular/platform-browser";
        import { HTTP_INTERCEPTORS } from "@angular/common/http";
        import { AppComponent } from "./app.component";
        import { TokenInterceptor } from "./token.interceptor";
        
        @NgModule({
          imports: [BrowserModule],
          declarations: [AppComponent],
          bootstrap: [AppComponent],
          providers: [
            {
              provide: HTTP_INTERCEPTORS,
              useClass: TokenInterceptor,
              multi: true, // <--- может быть зарегистрирован массив перехватчиков
            },
          ],
        })
        export class AppModule {}`
        
- Angular routing
- Angular forms
- Test dev