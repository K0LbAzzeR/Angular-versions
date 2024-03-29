# Angular-versions
История развития Angular (аля "Чего нового")
## 8.0.0 (2019-05-28)
### Поддержка TypeScript 3.4
### Ivy.
Ivy - это новый компилятор, а также новый движок рендеринга. Ivy может генерировать значительно меньшие бандлы, инкрементную компиляцию, а также является основой для будущих инноваций в Angular.

Если вы уже хотите попробовать Ivy, вы можете создать новый проект с ключем enable-ivy:
```
ng new ivy-project --enable-ivy
```
Данный ключ говрит CLI сохранить следующую запись в конфигурации tsconfig.app.json:
```json
"angularCompilerOptions": { 
        "enableIvy": true
}
```
### Новые фичи ngUpgrade
В службу локации был добавлен новый метод onUrlChange для отслеживания изменений URL-адресов:
```typescript
export class AppComponent {
  constructor(loc: Location, pLoc: PlatformLocation) {
    loc.onUrlChange((url) => console.debug('url change', url));
    console.debug('hostname: ', pLoc.hostname);
  }
}
```
Сервис PlatformLocation предлагает дополнительный доступ к отдельным частям URL-адреса. 
## 7.0.0 (2018-10-18)
### Поддержка TypeScript 3.1
### Поддержка RxJS 6.3
### Material Design.
Разработчики внесли небольшие изменения в дизайн платформы, руководствуясь принципами Material Design.
### Модуль ScrollingModule.
Позволяет загружать и удалять из DOM-структуры элементы, основываясь на их видимом списке.
### Модуль DragDropModule.
Создаёт автоматическую отрисовку нового порядка элементов при их перемещении.
### Пользовательские элементы.
Angular Elements поддерживает веб-стандарты для предупреждения о проектировочном контенте в пользовательских элементах:
```html
<my-custom-element>This content can be projected!</my-custom-element>
```
## 6.0.0 (2018-05-03)
### Поддержка TypeScript 2.7
### Поддержка RxJS 6.0
### Поддержка tslib 1.9
### Ivy Renderer
Ivy Renderer — это новый механизм рендеринга, который предназначен для обратной совместимости с существующим рендером и увеличения скорости рендеринга, он также оптимизирует размер финального пакета.
### Дополние navigationSource и restoreState в NavigationStart
В настоящее время в NavigationStart нет способа узнать, было ли выполнено принудительное инициирование навигации или изменение местоположения. При использовании navigationSource можно идентифицировать источник навигации, например, действие прокрутки или изменение URL / URI. restoreState предоставит восстановленный идентификатор навигации, который приведет к текущей навигации. Эти два свойства помогают нам обрабатывать несколько вариантов использования при маршрутизации.

NgModelChange — теперь это событие выдается после того, как значение и валидность обновляются в элементе управлении. Раньше он выдавалось перед обновлением. Поскольку теперь для него будет доступно обновленное значение элемента управления, обработчик станет более мощным.

Элемент управления формы statusChanges — Angular 6 выдает событие «PENDING», когда мы вызываем AbstractControl markAsPending.
### Комментарии в коде.
Поддержка одиночных, многострочных и jsdoc комментариев в коде.
### 
### 
### 
### 
### 
### 
## 5.0.0 (2017-11-01)
### Поддержка TypeScript 2.4
### Улучшенный компилятор
В Angular 4 компилятор перекомпилировал все файлы при каждом изменении. В Angular 5 компилятор работает только с теми файлами, в которых есть изменения.
### Оптимизированная сборка
В Angular CLI при использовании production build совместно с версией Angular 5 по умолчанию будет применяться build optimizer, который с помощью семантического анализа кода приложения сможет значительно уменьшить его размер.
### Новые события Router.
Используя события ActivationStart и ActivationEnd или ChildActivationStart и ChildActivationEnd, можно организовать отображения индикаторов загрузки при смене маршрута.
### HttpClient.
Новый HttpClient был добавлен в версии 4.3, старый http клиент помечен как depreceted в новой версии. В Angular 6 старый клиент будет удален. Из преимуществ нового клиента можно выделить самостоятельное извлечение JSON без необходимости явного применения метода map и возможность применять interceptors. https://angular.io/guide/http
### Валидация форм.
Теперь при работе с формами, c помощью свойства updateOn, можно определить, в какой момент будет происходить проверка – на событие blur или submit (вместо проверки на каждое событие input).
### Замена ReflectiveInjector на StaticInjector.
Изменен механизм для внедрения зависимостей. Для нового StaticInjector не нужен полифил Reflect (но при использовании JIT данные полифил все равно нужно будет использовать), что может уменьшить размер приложения.
### Улучшение NgZone.
NgZone стала еще быстрее, также библиотеку можно отключить для применения другой библиотеки для улучшения производительности.
### Улучшенный RxJS.
Поддержка обновлена до версии 5.5.2 и выше. Поддержка новых pipable operators https://github.com/ReactiveX/rxjs/blob/master/doc/pipeable-operators.md
## 4.0.0-rc.1 (2017-02-24)
### Поддержка TypeScript 2.1
### Улучшенные *ngIf и *ngFor
Теперь можно использовать if/else и создавать локальные переменные.
```html
<div *ngIf="userList | async as users; else loading">
 <user-profile *ngFor="let user of users; count as count" [user]="user">
 </user-profile>
<div>{{count}} total users</div>
</div>
<ng-template #loading>Loading...</ng-template>
```
### Angular Universal
Universal, проект, позволяющий запускать Angular на сервере, получил первое обновление. Большая часть его исходников находится в @angular/platform-server. Для знакомства с Angular Universal можно использовать новый метод renderModuleFactory в @angular/platform-server.
### Анимации
Анимации теперь обзавелись собственным пакетом @angular/platform-browser/animations.
### Шаблоны
#### ng-template вместо template
Тэг template устарел. Вместо него используйте ng-template.
### Сервисы
#### Meta
Для получения содержимого или обновления meta-тэгов был введен новый сервис:
```typescript
@Component({
  selector: 'ponyracer-app',
  template: `<h1>PonyRacer</h1>`
})
export class PonyRacerAppComponent {
constructor(meta: Meta) {
    meta.addTag({ name: 'author', content: 'Ninja Squad' });
  }
}
```
## 2.0.0 (2016-09-14)

Источник: https://github.com/angular/angular/blob/master/CHANGELOG.md
