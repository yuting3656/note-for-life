# 找 nested 的 element or 根本不知道 會跑出什麼樣子 html 的 template

## EX: 我只知道 auto complete 的時候 會生出 ngui-auto-complete 的tag

- 可用 `getAttribute('innerHTML')` 看內容物 html 是什麼

~~~ts

    step3AutoCompleteCompanyName = element(
            by.tagName('ngui-auto-complete'));

~~~


~~~typeScript
  it('[en] step 3 testing showing ngui-auto-complete tag', async () => {
        await step3CompanyName.sendKeys('test');
        expect(browser.wait(EC.presenceOf(step3AutoCompleteCompanyName), 5000)).toBe(true);
        browser.sleep(3000);
        // const test = await step3AutoCompleteCompanyName.all(by.tagName('li')).get(0);
        expect(step3AutoCompleteCompanyName.getAttribute('innerHTML')).toBe('kk');

    });

~~~

~~~node.js
  - Expected '<div class="ngui-auto-complete"><!--bindings={
    "ng-reflect-ng-if": "false"
  }--><!--bindings={
    "ng-reflect-ng-if": "true"
  }--><ul><!--bindings={
    "ng-reflect-ng-if": "false"
  }--><!--bindings={
    "ng-reflect-ng-if": "false"
  }--><!--bindings={
    "ng-reflect-ng-if": "false"
  }--><!--bindings={
    "ng-reflect-ng-if": null
  }--><!--bindings={}--><!--bindings={
    "ng-reflect-ng-for-of": "[object Object],[object Object",
    "ng-reflect-ng-for-track-by": "function (index, item) {\r\n    "
  }--><li class="item" ng-reflect-klass="item" ng-reflect-ng-class="[object Object]"><div style="color: black"><span>
        fdsaTEST
        </span></div></li><li class="item" ng-reflect-klass="item" ng-reflect-ng-class="[object Object]"><div style="color: black"><span>
        test11
        </span></div></li><li class="item" ng-reflect-klass="item" ng-reflect-ng-class="[object Object]"><div style="color: black"><span>
        test
        </span></div></li><li class="item" ng-reflect-klass="item" ng-reflect-ng-class="[object Object]"><div style="color: black"><span>
        fsfstest
        </span></div></li><li class="item" ng-reflect-klass="item" ng-reflect-ng-class="[object Object]"><div style="color: black"><span>
        test1111
        </span></div></li><li class="item" ng-reflect-klass="item" ng-reflect-ng-class="[object Object]"><div style="color: black"><span>
        Super Comp Test
        </span></div></li><li class="item" ng-reflect-klass="item" ng-reflect-ng-class="[object Object]"><div style="color: black"><span>
        testNO Comp cid
        </span></div></li><li class="item" ng-reflect-klass="item" ng-reflect-ng-class="[object Object]"><div style="color: black"><span>
        ggtest
        </span></div></li><li class="item" ng-reflect-klass="item" ng-reflect-ng-class="[object Object]"><div style="color: black"><span>
        test_good
        </span></div></li></ul></div>' to be 'kk'.
~~~

- 知道 auto 生成的 html 後就可以去抓抓

~~~typescript

        step3AutoCompleteCompanyName = element(
            by.className('ngui-auto-complete'));
~~~


~~~typeScript

    it('[en] step 3 testing showing ngui-auto-complete tag', async () => {
        await step3CompanyName.sendKeys('test');
        expect(browser.wait(EC.presenceOf(step3AutoCompleteCompanyName), 5000)).toBe(true);
        browser.sleep(3000)
        const result = await step3AutoCompleteCompanyName.all(by.tagName('li')).get(0).getText();
        expect(result) .toBe('fdsaTEST');
    });
~~~