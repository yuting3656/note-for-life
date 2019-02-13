SSL
=================
**Opting out**

For users who wish to opt out of certificate verification on a single connection, they can achieve this by providing the context argument to urllib.urlopen:

~~~python 
import ssl 
 # This restores the same behavior as before.
context = ssl._create_unverified_context()
urllib.urlopen("https://no-valid-cert", context=context)
~~~

It is also possible, `though highly discouraged`, to globally disable verification by monkeypatching the ssl module in versions of Python that implement this PEP:

~~~python
import ssl

try:
    _create_unverified_https_context = ssl._create_unverified_context
except AttributeError:
    # Legacy Python that doesn't verify HTTPS certificates by default
    pass
else:
    # Handle target environment that doesn't support HTTPS verification
    ssl._create_default_https_context = _create_unverified_https_context
~~~

*reference:*
`https://www.python.org/dev/peps/pep-0476/`

> 實例:
> 
> 在自家產品驗證的API:
>   - `'https://spaceadmin.hyweb.com.tw/rest/auth/admin/authentication'`
>
>       這個連結 (sysadmin, sysadmin) 要求 **SSL** 所以在程式寫法就變成
> 　
>  ~~~python
> self.context = ssl._create_unverified_context()
> 
> self.req = urllib.request.urlopen(self._url, self.data, context=self.context)
>  ~~~
>
> -  `http://space.hyweb.com.tw/rest/auth/user/authentication`
>
>     這個連結 (普通帳號) 要求 SSL 所以在程式寫法就變成
>
> ~~~python
> self.req = urllib.request.urlopen(self._url, self.data)
> ~~~
>    
> 
>  im 沒有要用到　context !如果不小心用到的話　會４０１　錯誤！
   
