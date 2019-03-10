toggle button
============

### HTML
~~~html 
<div class="category">
  <ul>
    <li *ngFor="let mbData of marketButtonDatas; let i=index;">
      <ng-container>
          <a 
            [ngClass]="{'active': mbData.status === true}"
            (click)="markCountryClick(mbData.name)">   
            {{mbData.name | translate}}</a>
      </ng-container> 
    </li>
  </ul>
</div>
~~~

### Component
~~~typescript
  markCountryClick(clickname: string) {
    this.marketButtonDatas.forEach( val => {
      if ( val.name === clickname) {
           val.status = true;
      } else {
        val.status = false;
      }
    });
  }
~~~

### data

~~~typescript
export class MarketButtonData {
  marketButtonData = [
    {
      'name': 'markets.as.button',
      'status': true
    },
    {
      'name': 'markets.na.button',
      'status': false
    },
    {
      'name': 'markets.oc.button',
      'status': false
    },
    {
      'name': 'markets.eu.button',
      'status': false
    },
    {
      'name': 'markets.me.button',
      'status': false
    },
    {
      'name': 'markets.ca.button',
      'status': false
    },
    {
      'name': 'markets.sa.button',
      'status': false
    },
    {
      'name': 'markets.af.button',
      'status': false
    },
  ];
}

~~~