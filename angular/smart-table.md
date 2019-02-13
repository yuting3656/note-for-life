客製化 回傳
====================

~~~ts

settings={
  actions: false,
  hideSubHeader: true,
  columns: {
      colElement1:{
          title: 'col name',
          filter: false,
          type: 'html',
          valuePrepareFunction: () => {
　　　　　　　return `回傳客製化的 Elements`;
          }
      },
      colElement2:{
        ...
      },
  } 

}

~~~

Table 的客製化
===========

~~~ts

 settings = { 
    mode: 'click-to-edit',

    selectMode: 'multi', // single | multi  
    actions: false,
    // 可以把多的　row 隱藏~~~
    hideSubHeader: true,
    // add: {
    //   addButtonContent: '<i class="nb-plus"></i>',
    //   createButtonContent: '<i class="nb-checkmark"></i>',
    //   cancelButtonContent: '<i class="nb-close"></i>',
    // },
    // edit: {
    //   editButtonContent: '<i class="nb-edit"></i>',
    //   saveButtonContent: '<i class="nb-checkmark"></i>',
    //   cancelButtonContent: '<i class="nb-close"></i>',
    //   confirmSave: true
    // },
    // delete: {
    //   deleteButtonContent: '<i class="nb-trash"></i>',
    //   confirmDelete: true,
    // },
    columns: {

      contry: {
        title: '國別',
        type: 'number',
        filter: false,
        // 客製化選單
        // editor:{
        //   type: 'list',
        //   config:{
        //     list: [{
        //       title: 'Taiwan',
        //       value: 'taiwan'
        //     }, {
        //       title: 'Japan',
        //       value: 'japan'
        //     }, {
        //       title: 'USA',
        //       value: 'usa',
        //     }, {
        //       title: 'Korea',
        //       value: 'korea'
        //     }]
        //   },
        // }
      },
      name: {
        title: '姓名',
        type: 'string',
        filter: false,
      },
      memberStatus:{
        title: '會員類型',
        type: 'string',
        filter: false,
      },
      tellphone: {
        title: '行動電話',
        type: 'string',
        filter: false,
      },
      email: {
        title: 'E-mail',
        type: 'string',
        filter: false,
      },
      phone: {
        title: '連絡電話',
        type: 'number',
        filter: false,
      },
      createDate: {
        title: '註冊時間',
        type: 'string',
        filter: false,
      },

      edit: {
        title: '維護',
        type: 'custom',
        filter: false,
        renderComponent: EditMembersButtonRenderComponent,
        valuePrepareFunction: (cell, row) => {
          console.log(row),
          console.log(cell)
        },
        // onComponentInitFunction: (instance) => {
        //   console.log(instance)
        // }
        // 調整寬度而~
        // width: '10%',
      }
    },
  };

~~~