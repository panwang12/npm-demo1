## 这是一个npm使用demo


### 常见命令
 * npm pack 生成tarball
 * npm link 创建symlink(符号链接),在本地目录执行,会在{prefix}/lib/      node_modules/下面生成 global package
 * npm link pack-name 会在当前目录生成global package 的链接
 * npm publish 发布包(public pkg ,private scoped pkg)
 * npm publish --access public 发布包(public scoped pkg)
 * npm versioin 1.0.1 更改当前版本
 * npm prefix 显示package.json或者node_moudle在的父目录
 * npm prefix -g 全局的

 ### package的创建流程
    1. npm int 创建package.json文件
    2. 新建js文件
    3. npm publish 发布

### package发布
    1. npm publish 如果是unscope package 就直接发布为public 如果是scope package 就发布为pravite
    2. npm publish --access public 如果为scope包就需要指定为public
### 撤销package
    1. npm unpublish [@scope-name/]pkg-name -f --otp=123456 在72小时内撤回发布的版本
        1. 其中otp为 two-authentication 验证
        2. 如果撤销在发布必须更新版本
    2. npm unpublish [@scope-name/]pkg-name@version -f --otp=123456 撤销某版本

### 弃用package
    1. 弃用安装包将在search result 检索不到,弃用提示会在package页面显示
    2. 弃用整个安装包
        1. npm deprecate pkg-name messagge  如果有使用 two-factor authentication 需要添加 --otp=123456
    3. 弃用某个版本
        1. npm deprecate pkg-name@version messagge  其他同上
    4. 如果包不想维护了,可以转为npm 拥有
        1. 命令1 npm owner add npm <package-name>   命令2 npm owner rm <user> <package-name> 
### 模块使用
    1. npm install pkg-name@version
    2. npm install pkg-name@version -g
    3. npm update
    4. npm outdated 输出版本信息
    5. npm outdated -g --depth=0 查看全局的包的版本情况

### 代码安全
    1.npm audit 可以在当前扫描安装包,并生成报告
    2.EAUDITNOLOCK错误处理
        1. npm i --package-lock-only 生成package-lock.json

### npm-config

#### 命令行flags
    1. 命令行 --foo bar 设置foo为bar,--foo 设置foo 为true
#### 环境变量
    1. npm_config_foo=bar 设置foo=bar,不区分大小写,NPM_CONFIG_FOO=bar同样
        *提示在npm-script内部,使用的变量有时会优先使用小写*




