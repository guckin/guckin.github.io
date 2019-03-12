---
layout: post
title:  "Angular Tour of Heroes"
date:   2019-03-04 00:55:00 -0800
categories: typescript
---

From [Tour of Heroes](https://angular.io/tutorial)

You can find the completed tutorial [here](https://github.com/guckin/angular-heroes-tour)

## 1. The Hero editor: 

Two way bindings:
[(ngModel)] is Angular's two-way data binding syntax
  ```html
  <div>
    <label>name:
      <input [(ngModel)]="hero.name" placeholder="name"/>
    </label>
  </div>
```

```
Template parse errors:
Can't bind to 'ngModel' since it isn't a known property of 'input'.
```

Angular needs the FormsModule.

```typescript
  import { FormsModule } from '@angular/forms';
```

FromModule needs to be imported within the AppModule

also...

Every component must be declared in exactly one NgModule.

So we need to declare our Hero component in NgModule

## 2. Displaying a List

`*ngFor` is the repeater directive.

For each of the heros let the hero hold the current hero.

```typescript
	<li *ngFor="let hero of heroes">
```

Now add a click event using `(click)` event

More of [Angulars event binding syntax](https://angular.io/guide/template-syntax#event-binding)

```typescript
<li *ngFor="let hero of heroes" (click)="onSelect(hero)">

```

Now the click event will call onSelect method on the component

So we need to implement that method on the component
```typescript
selectedHero: Hero;
onSelect(hero: Hero): void {
  this.selectedHero = hero;
}
```


`*ngIf` can be used to check conditions in the component

 Use class binding to do conditional styling, add `[class.selected]="some-condition"` to the element you want to style.
 
 
 
##3. Master/Detail Components

we can create comunication from one comment to another using bindings

```typescript 
<app-hero-detail [hero]="selectedHero"></app-hero-detail>
```

This passes the selected hero to the detail component which needs to take a hero. To do this we use the @Input decorator.

```typescript
@Input() hero: Hero;
```

We just refactored out the detail into its own component
 
 



