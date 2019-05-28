# standalone 

~~~html
<form>
   <input [(ngModel)]="person.food" [ngModelOptions]="{isModelProperty: false}">  <!-- Suggestion 1 -->
   <input [(ngModel)]="person.food" [ngModelOptions]="{isFormProperty: false}">  <!-- Suggestion 2 -->
   <input [(ngModel)]="person.food" [ngModelOptions]="{serialize: false}">  <!-- Suggestion 3-->
   <input [(ngModel)]="person.food" [ngModelOptions]="{standalone: true}">  <!-- Suggestion 4-->
</form>
~~~