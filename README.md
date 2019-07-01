# Angular-versions
История развития Angular (аля "Чего нового")

## 

## 4.0.0-rc.1 (2017-02-24)

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

### Поддержка TypeScript 2.1
Angular обновлён до более свежей версии TypeScript. Это улучшит скорость ngc и проверку типов.
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
