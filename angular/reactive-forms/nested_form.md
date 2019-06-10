# 有 object form 的 使用方法

- 建置 form 
~~~ts
    this.funcSerForm = this.fb.group({
      name: [, [Validators.required]], // 名稱
      engName: [, [Validators.required]], // 英文名稱
      serviceCode: [, [Validators.required]], // 代號
      serviceKey: [, [Validators.required]], // Service Key
      serviceRefCode: [, [Validators.required]], // 服務關聯代號
      // memberType: [, [Validators.required]], // 會員類型
      priority: [, [Validators.required]],　// 排序
      statementContent: [, [Validators.required]], // 服務介紹
      createDate: [], // 建立日期
      lastModifyDate: [], // 上次修改日期
      status: [, [Validators.required]], // 狀態
      localeName: [JSON.stringify('en:{ name: \'TestBed\', }'),], // i18n
      domain: [],
      sid: [],
      modifierId: [],
      modifierName: [],
      creatorId: [],
      creatorName: [],
      memberAccessAttrs: this.fb.group({
        contactMobilePhoneVerified: [],
        memberType: [],
        nickNameRequired: []
      }),
    });
~~~



- html 
~~~html
<form [formGroup]="funcSerForm">
    ..............

   <div class="form-group" [formGroup]="funcSerForm.get('memberAccessAttrs')">
        <label class="control-label col-md-3 col-sm-3 col-xs-12">是否需要會員手機認證？</label>
          <div class="col-md-6 col-sm-6 col-xs-12">
              <div id="gender" class="btn-group" data-toggle="buttons">
                  <input type="radio" class="flat" formControlName="contactMobilePhoneVerified" value="Y" checked=""
                required />
              &nbsp;
              是 &nbsp;
              <input type="radio" class="flat" formControlName="contactMobilePhoneVerified" value="N" checked=""
                required />
              否
            </div>
          </div>
        </div>

    .....................
</form>

~~~
