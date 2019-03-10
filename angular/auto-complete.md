# ngui-auto-complete

## 安裝

   > npm install @ngui/auto-complete --save


## Link 

   > https://github.com/ng2-ui/auto-complete/blob/master/README.md


## 實例

~~~typescript
// auto-complete:　[source]="dataSource$.bind(this)"
  dataSource$ = (keyword: string): Observable<any> => {
    if (keyword.length >= 2) {
      return this.xxxSrv.checkXxxxxName(keyword).pipe(
        map((result: any) => {
          return result;
        }),
      );
    }
    return of([]);
  }
~~~

