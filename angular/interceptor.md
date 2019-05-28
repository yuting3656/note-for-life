# angular interceptor

~~~ts
@NgModule({
    providers: [
        {
           provide: HTTP_INTERCEPTORS,
           useClass: AuthInterceptor,
           multi: true,
        }
    ]})
~~~