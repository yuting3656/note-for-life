# FormData Example


~~~html
      <input #fileInput type="file" (change)="onFileInput($event)" style="display: none;">

~~~
~~~ts

  onFileInput($event) {
     try {
      if ($event.target.files && $event.target.files[0]) {
        const file = $event.target.files[0];
        this.uploadImage = $event.target.files[0];
        const reader = new FileReader();
        reader.onload = e => this.imageUrl = reader.result;
        reader.readAsDataURL(file);
      } else {
        this.imageUrl = './assets/images/default-user.jpg';
      }
     } catch {}
  }

if (!this.uploadImage) {
     return;
    }
    this.dialToggle();
    this.spinnerSer.showSpinner();
    const formData = new FormData();
    formData.append('file', this.uploadImage);
    this.memberProPhotoSer.updateUserProfilePhoto(formData).subscribe( () => {
      location.reload();
    },
~~~