map 練習
=============================================


~~~ts
import { pairwise, take, map } from 'rxjs/operators';

// interval(1000).subscribe(console.log)
interval(1000).pipe(
  map( value => {
    if( value % 5 ==0 ){
      // return  console.log('YA')
      return 'YA'
    }else{
       return value
    }
  })
).subscribe(console.log)
~~~