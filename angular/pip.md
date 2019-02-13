Pipe 在 Component Class 裡的使用
===============================
> Pipe 檔案

~~~ts
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'capitalize'
})
export class CapitalizePipe implements PipeTransform {
  transform(value: string, args?: any): any {
    return value.split(' ').map(word => {
      return word.length > 2 ? word[0].toUpperCase() + word.substr(1) : word;
    }).join(' ');
  }
}
~~~


> Class 檔案

~~~ts
// ...
import { CapitalizePipe } from './capitalize.pipe';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css'],
  providers: [ CapitalizePipe ] // -------> 別忘了要把 Pipe 加入 providers!!!!!!
})
export class AppComponent {

  constructor(private capitalize: CapitalizePipe) {}

  // ...
}
~~~

> Class 檔案裡的 method

~~~ts
onSubmit(value) {
  this.data = this.capitalize.transform(value);
  // ...
}
~~~



> 工作實例:
~~~ts
import { Component, OnInit } from '@angular/core'; 
import { SeatService } from '../../shared/services/seat.service'; 
import { BookingsService } from '../../shared/services/bookings.service'; 
import { NavigationExtras, Router } from '@angular/router'; 
import { ErrorService } from '../../shared/services/error.service'; 
import { UniquePipe } from '../../unique.pipe'; 

@Component({ 
  selector: 'app-on-site-seat', 
  templateUrl: './on-site-seat.component.html', 
  styleUrls: ['./on-site-seat.component.css'], 
  providers: [UniquePipe] 
}) 
export class OnSiteSeatComponent implements OnInit { 
  seatArray: any = []; 
  modalSeatName = ''; 
  availableTime: any; 
  locationName: string; 
  loading = true; 

  MURA: any = []; 
  MURB: any = []; 
  MURC: any = []; 
  constructor( 
    private errorService: ErrorService, 
    private router: Router, 
    private seatService: SeatService, 
    private bookingsService: BookingsService, 
    private unique: UniquePipe 
  ) { } 

  ngOnInit() { 
    const cateId = sessionStorage.getItem('cateId'); 
    // const type = sessionStorage.getItem('type'); 
    const locationId = sessionStorage.getItem('locationId'); 
    this.locationName = sessionStorage.getItem('locationName'); 

    // this.seatService.getSeatStatus('SET', locationId, cateId) 
    this.seatService.getSeatStatus(sessionStorage.getItem('cid')) 
      .subscribe(data => { 

        for (let i = 0; i < data.length; i++) { 
          // const y = this.seatArray.findIndex(x => x.name === data[i].name); 
          // if (y <= -1) { 
          // this.seatArray.push(data[i]); 
          // } 
          // // // 存進陣列 
          this.seatArray[i] = data[i]; 

        } 
        alert(this.seatArray + 'component'); 
      }, 
        () => { }, 
        () => { 
          this.mapSeatObj(this.seatArray); 
        }); 
  } 

  mapSeatObj(seatArray: any) { 
    console.log(this.seatArray); 
    let modalSwitch: boolean; 
    for (let i = 0; i < seatArray.length; i++) { 
      let classList = 'movie'; 
      const status = seatArray[i].status; 
      const councilBookings = seatArray[i].councilBookings.length; 
      let bookingEndDate: any = 0; 
      let councilstatus: string; 

      if (councilBookings !== 0) { 
        const endDate: any = new Date(seatArray[i].councilBookings[0].bookingEndDate); 
        const nowDate: any = new Date(); 
        councilstatus = seatArray[i].councilBookings[0].status; 
        // 結束時間-現在時間 轉換成分鐘數 
        bookingEndDate = Math.ceil((endDate - nowDate) / 60000); 
      } 
      switch (status) { 
        // case:Y 座位開放 
        case 'Y': 
          if (councilBookings === 0) { // 無預約紀錄 
            modalSwitch = true; 
            break; 
          } else if (bookingEndDate <= 15) { // 距離結束時間<15分鐘 
            modalSwitch = false; 
            classList += ' Ending'; 
            break; 
          } else if (councilstatus === 'L') { // 暫離 
            modalSwitch = false; 
            classList += ' Leave'; 
            break; 
          } else { // 有預約紀錄 
            modalSwitch = false; 
            classList += ' Reserved'; 
            break; 
          } 
        // case:N 座位不開放 
        case 'N': 
          modalSwitch = false; 
          classList += ' Not-open'; 
          break; 
      } 
      this.seatArray[i].className = classList; 
      this.seatArray[i].modalSwitch = modalSwitch; 

    } 
    this.seatArray = this.unique.transform(this.seatArray); 
    this.loading = false; 
  } 

  getSeatInfo(seatName: string, rid: string) { 
    this.modalSeatName = seatName; 
    // if ((location.href).match('registration') !== null) { 
    this.availableTime = sessionStorage.getItem('useupperlimit'); 
    // console.log(this.seatArray, '11111'); 
    sessionStorage.setItem('rid', rid); 
    // this.action = '使用' 
  } 

  // 自行選位 
  userSeat() { 
    const date = new Date(); 
    const day = this.seatService.yyyymmdd(date); 
    const now = date.getHours() + ':' + (date.getMinutes() - 1) + ':' + date.getSeconds(); 
    const useTime = parseFloat(sessionStorage.getItem('useupperlimit')); 
    let endMin = date.getMinutes() + ((useTime - Math.floor(useTime)) * 60) - 1; 
    let endHour = date.getHours() + Math.floor(useTime); 
    if (endMin >= 60) { 
      endHour += 1; 
      endMin -= 60; 
    } 
    const endTime = endHour + ':' + endMin + ':' + date.getSeconds(); 
    // 判斷是否超過閉館時間 

    const bookingStartDatePost = day + ' ' + now; 
    const bookingEndDatePost = day + ' ' + endTime; 

    const data = { 
      cateId: sessionStorage.getItem('cateId'), 
      bookingStartDate: bookingStartDatePost, 
      bookingEndDate: bookingEndDatePost, 
      mainResourceId: sessionStorage.getItem('rid'), 
    }; 

    this.bookingsService.makeSure(data) 
      .subscribe(res => { 
        const bid = res.bid; 
        const bookingResult: NavigationExtras = { 
          queryParams: { 
            'title': '完成登記', 
            'hostName': res.hostName, 
            'bookingStartDate': res.bookingStartDate, 
            'bookingEndDate': res.bookingEndDate, 
            'type': res.type, 
            'seat': res.mainResourceName 
          } 
        }; 

        this.bookingsService.useStart(bid).subscribe( 
          result => { 
            this.router.navigate(['/on-site/result'], bookingResult); 
          } 
        ); 
      }, 
        error => { 
          const errorBody = JSON.parse(error._body); 
          let msg: string; 
          if ((errorBody.message).indexOf('Double') !== -1) { 
            // 重複登記 
            msg = '重複登記'; 
          } else if ((errorBody.message).indexOf('Already') !== -1) { 
            // 座位已被登記 
            msg = '座位已被登記'; 
          } else if ((errorBody.message).indexOf('Member') !== -1) { 
            // 使用者被停權 
            msg = '您已被停權，請洽櫃台'; 
          } else if ((errorBody.code).indexOf('CouncilBookingOpeningDateExceedException') !== -1) { 
            // 超出預約時間 
            msg = '已超過圖書館開放時間'; 
          } else { 
            msg = '登記座位失敗'; 
          } 
          this.errorService.changeMessage(msg); 

        }, 
        () => { }); 
  } 

  getSeat() { 
    // this.countObj = this.seatService.getCount(); 
    this.seatService.getResourceData() 
      .subscribe(resp => { 
        for (let i = 0; i < resp.length; i++) { 
          const roomType = resp[i].name.substr(0, 1); 

          switch (roomType) { 
            case 'A': 
              this.MURA.push(resp[i]); 
              break; 
            case 'B': 
              this.MURB.push(resp[i]); 
              break; 
            case 'C': 
              this.MURC.push(resp[i]); 
              break; 
          } 
        } 
      }, 
        () => { }, 
        () => { }); 
  } 
}
~~~


> Pipe 檔案

~~~ts 
import { Pipe, PipeTransform } from '@angular/core'; 
// import * as _ from 'lodash'; 
@Pipe({ 
  name: 'unique', 
  pure: true 
}) 
export class UniquePipe implements PipeTransform { 

  transform(value: any): any { 

    window.alert(value + 'pipe'); 
    
    const seatArray = []; 
    value.filter(item => { 
      const y = seatArray.findIndex(x => x.name === item.name); 
      if (y <= -1) { 
        seatArray.push(item); 
      } 
    }); 
    return seatArray; 
  } 
}
~~~