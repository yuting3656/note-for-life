# 邊上傳邊預覽照片！！！

> link: https://stackoverflow.com/questions/50482814/image-preview-before-upload-in-angular-5

~~~ts
  onFileInput($event) {
     console.log($event);
     try {
      if ($event.target.files && $event.target.files[0]) {
        const file = $event.target.files[0];
        const reader = new FileReader();
        reader.onload = e => this.imageUrl = reader.result;
        reader.readAsDataURL(file);
      } else {
        this.imageUrl = './assets/images/default-user.jpg';
      }
     } catch {}
  }
~~~

~~~html
      <div class="profile_photo_div profile_button">
        <div class="profile_button">
          <img [src]="imageUrl || defaultImgUrl" height="200">
        </div>
            <button type="button" class="btn btn-blue" (click)="fileInput.click()" style="display: end;">
               上傳照片
                <input #fileInput type="file" (change)="onFileInput($event)" style="display: none;">
            </button>
      </div>
~~~