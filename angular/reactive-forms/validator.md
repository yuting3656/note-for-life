自己刻　custom 的　validator [1]
==========

## Component code

~~~ typeScript

xxxFormFroup = this._formBuilder.group({
      verifyIdInput: ['', [Validators.required, verifyIdValidator]],
    });



// custom email validator
export function customValidator(input: FormControl) {
  if (input.value === 'hyweb@taitra.org.tw') {
    return { customValidator: {
      value: false
    }};
  }
}

~~~

## html Code

~~~html
<mat-form-field class="full-width">
    <input 
          matInput
          formControlName="accountEmail"
          placeholder="帳號(eamil)"
          required
          >
    <mat-icon 
              matSuffix
              class="material-icons">
              mail_outline</mat-icon>
    <mat-error *ngIf="firstFormGroup.get('accountEmail').hasError('required')">請輸入帳號(email)</mat-error>
    <mat-error *ngIf="firstFormGroup.controls['accountEmail'].hasError('customValidator')">email已經有人使用</mat-error>
 </mat-form-field>

~~~


自己刻　custom 的　validator [2]
==========

## Component code

~~~ typeScript

  /*
   *  step 1 form:
   *  variables: eamil, password, confirmPassword
   */
  step1Form = this.fb.group({
    email: [this.formDataSer.getEmail(), [Validators.required, Validators.email]],
    password: ['', [Validators.required]],
    confirmPassword: ['', [Validators.required]],
    recaptcha: ['', [Validators.required]],
    regCompStatus: [, []],
    regIndivStatus: [, []]
  }, { validators: this.checkPasswords});

  /**
   * check password ths same
   */
  checkPasswords(group: FormGroup) {
    const password = group.controls.password.value;
    const confirmPassword = group.controls.confirmPassword.value;
    return password === confirmPassword ? null : { notSame: true };
  }
~~~

## html Code

~~~html
        <div class="form_grp">
              <label for="password" class="form_title"><abbr class="necessary" title="為必填(選)欄位,不能為空白。">*</abbr>確認密碼</label>
              <div class="form_content">
                <input formControlName="confirmPassword" name="password" type="password" placeholder="請輸入密碼" required>
                <div *ngIf="step1Form.hasError('notSame')" class="notice_error">密碼不一致</div>
              </div>
            </div>
~~~