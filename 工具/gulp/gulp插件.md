# gulp插件

- 编译Sass (gulp-ruby-sass)

- Autoprefixer (gulp-autoprefixer)

- 缩小化(minify)CSS (gulp-minify-css)

- JSHint (gulp-jshint)

- 拼接 (gulp-concat)

- 丑化(Uglify) (gulp-uglify)

- 图片压缩 (gulp-imagemin)

- 即时重整(LiveReload) (gulp-livereload)

- 清理档案 (gulp-clean)

- 图片快取，只有更改过得图片会进行压缩 (gulp-cache)

- 更动通知 (gulp-notify)


	// 载入外挂
	var gulp = require('gulp'),  
	    sass = require('gulp-ruby-sass'),
	    autoprefixer = require('gulp-autoprefixer'),
	    minifycss = require('gulp-minify-css'),
	    jshint = require('gulp-jshint'),
	    uglify = require('gulp-uglify'),
	    imagemin = require('gulp-imagemin'),
	    rename = require('gulp-rename'),
	    clean = require('gulp-clean'),
	    concat = require('gulp-concat'),
	    notify = require('gulp-notify'),
	    cache = require('gulp-cache'),
	    livereload = require('gulp-livereload');
	
	// 样式
	gulp.task('styles', function() {  
	  return gulp.src('src/styles/main.scss')
	    .pipe(sass({ style: 'expanded', }))
	    .pipe(autoprefixer('last 2 version', 'safari 5', 'ie 8', 'ie 9', 'opera 12.1', 'ios 6', 'android 4'))
	    .pipe(gulp.dest('dist/styles'))
	    .pipe(rename({ suffix: '.min' }))
	    .pipe(minifycss())
	    .pipe(gulp.dest('dist/styles'))
	    .pipe(notify({ message: 'Styles task complete' }));
	});
	
	// 脚本
	gulp.task('scripts', function() {  
	  return gulp.src('src/scripts/**/*.js')
	    .pipe(jshint('.jshintrc'))
	    .pipe(jshint.reporter('default'))
	    .pipe(concat('main.js'))
	    .pipe(gulp.dest('dist/scripts'))
	    .pipe(rename({ suffix: '.min' }))
	    .pipe(uglify())
	    .pipe(gulp.dest('dist/scripts'))
	    .pipe(notify({ message: 'Scripts task complete' }));
	});
	
	// 图片
	gulp.task('images', function() {  
	  return gulp.src('src/images/**/*')
	    .pipe(cache(imagemin({ optimizationLevel: 3, progressive: true, interlaced: true })))
	    .pipe(gulp.dest('dist/images'))
	    .pipe(notify({ message: 'Images task complete' }));
	});
	
	// 清理
	gulp.task('clean', function() {  
	  return gulp.src(['dist/styles', 'dist/scripts', 'dist/images'], {read: false})
	    .pipe(clean());
	});
	
	// 预设任务
	gulp.task('default', ['clean'], function() {  
	    gulp.start('styles', 'scripts', 'images');
	});
	
	// 看手
	gulp.task('watch', function() {
	
	  // 看守所有.scss档
	  gulp.watch('src/styles/**/*.scss', ['styles']);
	
	  // 看守所有.js档
	  gulp.watch('src/scripts/**/*.js', ['scripts']);
	
	  // 看守所有图片档
	  gulp.watch('src/images/**/*', ['images']);
	
	  // 建立即时重整伺服器
	  var server = livereload();
	
	  // 看守所有位在 dist/  目录下的档案，一旦有更动，便进行重整
	  gulp.watch(['dist/**']).on('change', function(file) {
	    server.changed(file.path);
	  });
	
	});