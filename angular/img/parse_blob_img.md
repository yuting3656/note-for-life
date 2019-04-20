# javascript angular 傳照片超級帥的兒方法!!!!


~~~ts
  this.funcServicesSer.checkLogo(this.currentSid).subscribe((res) => {
            console.log(res);
            // this.createImageFromBlob(res);
            const blob = new Blob([res], { type: 'image:jpg/image:png' });
            const urlCreator = window.URL;
            this.testImg = this.sanitizer.bypassSecurityTrustUrl(urlCreator.createObjectURL(blob));
            console.log(blob)
          });
~~~

