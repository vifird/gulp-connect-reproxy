# gulp-connect-reproxy
A simple proxy middleware for gulp-connect

# How to use
```javascript

gulp.task('connect', function () {
    connect.server({
        root: "build",
        port: 9000,
        livereload: true,

        middleware: function (connect, options) {

            var Reproxy = require('gulp-connect-reproxy');

            options.rule = [/.do/, /.jsp/, /.htm/];
//or        options.rule = /.do/;

            options.server = "127.0.0.1:8081";

            var proxy = new Reproxy(options);

            return [proxy];
        }
    });
});
```


## Notes:
```
@ options.rule
    • Array or String of Regular Expression
@ options.server
    • a server host name to proxy
```

## Example

If we config it like this
```
    @options : {
        rule : /.do/,
        server : "127.0.0.1:8081"
    }
```
when we request "http://127.0.0.1:9000/user/edit.do",<br/>
    the proxy server will work and the URL will be redirected to "http://127.0.0.1:8001/user/edit.do";<br/>
but when we requrest "http://127.0.0.1:9000/user/user.js",<br/>
    it will not work.


## User
Name : Bin Zhang<br/>
From : Beijing China
