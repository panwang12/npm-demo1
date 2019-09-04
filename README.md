## 这是一个npm使用demo


### 常见命令
 * npm pack 生成taball
 * npm link 创建symlink(符号链接),在本地目录执行,会在{prefix}/lib/node_modules/下面生成 global package
 * npm link pack-name 会在当前目录生成global package 的链接
 * npm publish 发布包(public pkg ,private scoped pkg)
 * npm publish --access public 发布包(public scoped pkg)


 ### package的创建流程
    1. npm int 创建package.json文件
    2. 新建js文件
    3. npm publish 发布