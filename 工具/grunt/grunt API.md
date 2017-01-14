# grunt

### 安装CLI

全局安装
    
    npm install -g grunt-cli
    
执行上述命令后，`grunt`命令就加入到你的系统路径中了，以后在任何目录下都可以执行此命令。

>   注意，安装了`grunt-cli`不等于安装好了`Grunt`
>   `Grunt CLI`的任务很简单：调用与`Gruntfile`在同一目录中`Grunt`。这样带来的好处是，允许你在同一个系统上同时安装多个版本的`Grunt`。

### CLI的作用

每次运行`grunt`时，它就会利用node提供的`require()`查找本地安装的`grunt`。

如果找到一份本地安装的`grunt`，`CLI`就将其加载，并传递`Gruntfile`中的配置信息，然后执行你所指定的任务。

### 安装grunt及其插件

    npm install grunt --save-dev
    npm install grunt-* --save-dev
    
### gruntfile

Gruntfile由以下几部分构成

- "wrapper" 函数
- 项目与任务配置
- 加载grunt插件和任务
- 自定义任务

#### gruntfile文件示例

    module.exports = function(grunt) {
    
      // Project configuration.
      grunt.initConfig({
        pkg: grunt.file.readJSON('package.json'),
        uglify: {
          options: {
            banner: '/*! <%= pkg.name %> <%= grunt.template.today("yyyy-mm-dd") %> */\n'
          },
          build: {
            src: 'src/<%= pkg.name %>.js',
            dest: 'build/<%= pkg.name %>.min.js'
          }
        }
      });
    
      // 加载包含 "uglify" 任务的插件。
      grunt.loadNpmTasks('grunt-contrib-uglify');
    
      // 默认被执行的任务列表。
      grunt.registerTask('default', ['uglify']);
    
    };
    
`"wrapper" 函数`

每一份 Gruntfile （和grunt插件）都遵循同样的格式，你所书写的Grunt代码必须放在此函数内：

    module.exports = function(grunt) {
      // Do grunt-related things in here
    };
    
`项目和任务配置`





