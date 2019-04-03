# 路徑設定 注意事項

~~~ts
domain = 'https:www.yuting.sogood.com';

/**
 *  相對路徑
 */
url = 'rest/app'; // === './rest/app';  

/**
 * 從根目錄開始
 */
url_1 = '/rest/app';

/*
 * 當使用者在 https://www.yuting.sogood.com/member/app
 * 的 url 下觸發下面的 request
 */
HttpClient.get(`${url}`) // --->  送出: https://www.yuting.sogood.com/member/app/rest/app
HttpClient.get(`${url_1}`) // ---> 送出:  https://www.yuting.sogood.com/rest/app 

~~~