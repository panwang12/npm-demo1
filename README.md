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
 * npm bin 显示当前bin目录的位置
 * npm bin -g 显示全局bin目录位置
 * npm login  登录用户
 * npm whoami 显示登录的用户

### 操作npm缓存
 * npm cache add "tarbal file/folder/tarbal url/name@version" 添加一个缓存
 * npm cache clean -f 清除缓存
 * npm cache verify 检查缓存
 * ~/.npm 缓存文件保存位置
 ### npm-folder
 * ./node_modules 本地包位置 
 * {prefix}/lib/node_modules(unix) {prefix}/node_modules(window) 全局包位置
 * {prefix}/bin(unix) {prefix}(window)  可执行js文件的位置


### package的创建流程
 1. npm int 创建package.json文件
 2. 新建js文件
 3. npm publish 发布

### package发布
 1. npm publish 如果是unscope package 就直接发布为public 如果是scope package 就发布为pravite
 2. npm publish --access public 如果为scope包就需要指定为public

### 撤销package
 1. npm unpublish [@scope-name/]pkg-name -f --otp=123456 在72小时内撤回发布的版本
  * 其中otp为 two-authentication 验证
  * 如果撤销在发布必须更新版本
 2. npm unpublish [@scope-name/]pkg-name@version -f --otp=123456 撤销某版本

### 弃用package
 1. 弃用安装包将在search result 检索不到,弃用提示会在package页面显示
 2. 弃用整个安装包
  * npm deprecate pkg-name messagge  如果有使用 two-factor authentication 需要添加 --otp=123456
 3. 弃用某个版本
  * npm deprecate pkg-name@version messagge  其他同上
 4. 如果包不想维护了,可以转为npm 拥有
  * 命令1 npm owner add npm <package-name>   
  * 命令2 npm owner rm <user> <package-name> 
### 模块使用
 1. npm install pkg-name@version
 2. npm install pkg-name@version -g
 3. npm update
 4. npm outdated 输出版本信息
 5. npm outdated -g --depth=0 查看全局的包的版本情况

### 代码安全
 1. npm audit 可以在当前扫描安装包,并生成报告
 2. EAUDITNOLOCK错误处理
   * npm i --package-lock-only 生成package-lock.json

### npm-config
 1. npm config ls -l 查看npm配置的列表 -l是查看更多
 2. 命令行输入 --foo=bar 设置foo为bar
 3. 程序中通过 process.env.npm_config_foo来取值
 4. .npmrc是npm 的一个配置文件
 5. 获取package.json的配置项,process.env.npm_package_filedName 
 6. npm config set foo:port 80 设置package.json name字段为foo的config字段的port值
### npm-script
 1. package.json的scripts字段
 2. 当依赖的模块含有可执行脚本,在npm install时候将会添加到node_moudles/.bin

### package.json
 1. files字段, 是一个数组,包含的文件在npm pack 的时候会打成tarball,如果作为依赖包,可以供用户安装使用
  * 默认包含package.json/README/CHANGES / CHANGELOG / HISTORY/LICENSE / LICENCE/NOTICE/The file in the “main” field
  * 默认不包含......省略.....
 2. bin 让js文件可执行 
  * config包含 { "bin" : { "myapp" : "./cli.js" } }
  * 可执行文件第一行 #!/usr/bin/env node, 保证可执行文件使用node执行
  * 安装包时候创建symlink到 prefix/bin或者 ./node_modules/.bin/
 3. peerDependencies,如果当前包被当做依赖,当前环境需要安转peerdependencies


