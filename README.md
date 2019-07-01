# Angular-versions
История развития Angular (аля "Чего нового")

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
