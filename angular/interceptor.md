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

~~~ts
@Injectable({
    providedIn: 'root'
})
export class ResponseInterceptor implements HttpInterceptor {

    constructor(private router: Router) {
    }

    intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
        return next.handle(req).pipe(
            catchError((error) => this.handleError(error))
        );
    }

    handleError(error): Observable<HttpEvent<any>> {
        console.log('from interceptor error', error);
        if (error instanceof HttpErrorResponse) {
            if (error.status === 401) {
                // alert('登入逾時，請重新登入');
                this.router.navigate(['/login']);
            }
            return throwError(error);
        }

        return throwError(error);
    }

}
~~~