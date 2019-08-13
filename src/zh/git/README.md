*github
1. github是一个项目托管平台
2. github支持两种协议：https ssh
ssh协议：需要配置公钥和秘钥。
ssh-keygen  生成公钥秘钥。
https协议：需要用客户名和密码



命令 | 意义
---|---
git remote add origin 地址 | 连接仓库
git remote -v | 查看仓库
git push -u origin maseter | 本地版本库所有的修改提交到网上
git pull origin master | 把远程仓库的代码拉取到本地仓库
git branch 分支名 | 新建分支
git branch | 查看本地的分支
git checkout 分支名 | 切换分支
git checkout -b 分支名 | 创建并切换分支
git merge 分支名 | 合并分支
git bransh -d 分支名 | 删除分支
git branch -a | 查看本地和远程所有的分支
git branch -r | 查看远程的分支
git push origin -d 分支名 | 删除远程的分支

```
git merge: 合并代码
git pull = git fetch + git merge
```


3. **gulp.serise(task1,task2,...)** 设置任务的执行顺序   **串行执行**
4. **gulp.parallel(task1,task2,...)** 设置任务的执行顺序  **并行执行**
5. **gulp.watch(globs,gulp.serise/gulp.parallel(task1,task2,...)) 监听文件变化，执行任务**
6. 

插件 | 说明
---|---
gulp-sass | 编译scss
gulp-less | 编译less
gulp-autoprefixer | 添加前缀
gulp-clean-css | 压缩css文件
gulp-uglify | 压缩js
gulp-webserver | 起服务
gulp-babel  | ES6 -> ES5
gulp-htmlmin | 压缩html
gulp-concat 注意：使用时括号内为合并后的文件名 | 合并文件
browser-sync | 起服务
gulp-rev | 生成文件后缀
gulp-rev-collector | 替换文件路径


```
**防止缓存**
var gulp = require('gulp');
var rev = require('gulp-rev');
var collector = require('gulp-rev-collector');
gulp.task('rev', function() {
    return gulp.src('./src/js/index.js')
        .pipe(rev()) //添加后缀
        .pipe(gulp.dest('./src/js'))
        .pipe(rev.manifest()) //生成替换文件 json
        .pipe(gulp.dest('./src/bulid')) //替换文件json的位置
})
gulp.task('collector', function() {
    return gulp.src(['./src/bulid/*.json', './src/index.html']) //进行替换 先 json 后 html
        .pipe(collector({
            replaceRev: true //开始替换
        }))
        .pipe(gulp.dest('./src'))
})

**两种起服务的方式**
gulp.task('server',functiong(){
    retuen browserSync{
       server:{
            baseDir:'src',
            middleware:function(){
                //拦截请求
            }
       },
       port:9090,
       files:[true] //自动刷新
    }
})  



gulp.task('server',function(){
    return gulp.src('src')
    .pipe(server(){
        port:9090  //设置端口号
        open:true  //自动打开浏览器
        livereload:true  //自动刷新浏览器
        host:   //配置ip的 透过手机来测试
        fallback:'demo.html'   //指定默认的打开文件
        middleware:function(req,res,next){  //拦截前端请求
        var pathname = url.parse(req.url).pathname;
            if(){
                
            }else{
                
            }
        }
    })
})

-webkit-overflow-scrolling:touch;
解决苹果scroll的兼容问题
```