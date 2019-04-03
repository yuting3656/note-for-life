formArray real example
=====

> TS example

~~~typeScript

// interestedMarketForm
  interestedMarketForm = this.fb.group({
    markets: new FormArray([])
  });


 // oninit
 ngOnInit() {
     this.patchMarketData();
 }

 // patch value
 patchMarketData() {
    const marketsItem: FormArray = this.interestedMarketForm.get('markets') as FormArray;
    // currentDisplayOptions 就是你要顯示的項目
    for (const option of this.currentDisplayOptions) {
      marketsItem.push(this.fb.group({
        id: option.id,
        name: option.name,
      }));
    }
  }

~~~

> HTML example

~~~html
      <ng-container *ngFor="let marketOption of currentDisplayOptions| slice:0; let i=index">
        <label formArrayName="markets">
          <input 
             name=""
             type="checkbox"
             value="{{marketOption.id}}"
             [formGroupName]="i"
            (change)="updateMarketValues(marketOption.id, $event)"
            [checked]="checkMarketValues(marketOption.id)"
            >{{marketOption.name | translate}}
        </label>
      </ng-container>
~~~