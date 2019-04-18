# ngChange and ngModelChange different


> link: `https://stackoverflow.com/questions/44840735/change-vs-ngmodelchange-in-angular`

- (change) --> 就是最普通的 change event 看 html 的 type 和 user 的 操作而做出回應
    *  [MDN HTMLElement: change event 相關連結](https://developer.mozilla.org/en-US/docs/Web/Events/change)
    ~~~html
    <input (change)="somethingChanged()">
    ~~~
    ~~~html
     <select (change)="changed($event)">
    <option *ngFor="let currentData of allData" [value]="currentData.id">
        {{data.name}}
    </option>
    </select>
    ~~~
    ~~~TS
    changed(e){
    // event comes as parameter, you'll have to find selectedData manually
    // by using e.target.data
    }
    ~~~

- (ngModelChange) --> **必須**要有 ngModel directive, 因為 (ngModelChange) 是 ngModel directive 的 @Output, 當 ngModel 改變的時候 (ngModelChange) 會被觸發! 
    ~~~html
    <select [(ngModel)]="data" (ngModelChange)="dataChanged($event)" name="data">
    <option *ngFor="let currentData of allData" [ngValue]="currentData">
        {{data.name}} </option>
    </select>
    ~~~
    ~~~TS
    dataChanged(newObj) {
    // here comes the object as parameter
    }
    ~~~