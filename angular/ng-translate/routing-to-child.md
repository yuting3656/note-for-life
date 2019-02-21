從 root　module 到　chile module 使用同一個　TranslateModule　 
================

- 相關連結

    > `https://github.com/ngx-translate/core/issues/590`

- 解釋
  
    > I solved it. The thing was that my component has been linked through routing and not selector. In that case, you are supposed to provide TranslateModule in the routing module.

- 實例

~~~typescript

app.module
    |
    |--- main-content.module / main-content-routing.module
    |            |
    |            |---taitraApps.module
                 |---memberInfo.module
                 |---accountSetting.module
                 |---interestIssues.module


@NgModule({
  imports: [
    RouterModule.forChild(routes),
    TranslateModule,
  ],
  exports: [
    RouterModule,
    TranslateModule
  ]
})
export class MainContentRoutingModule { }
~~~