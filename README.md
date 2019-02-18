# cus_babel-plugin-istanbul

基于业务需求，对原有的babel-plugin-istanbul进行定制修改
#### 1 定制instrument后，文件路径的显示。原有逻辑是插件内直接获取的file.opts.filename——改为可根据业务需求，进行配置。
#### 2 原有插件默认对语句，方法，和逻辑分支都进行插桩。——为平衡业务诉求和对应用的性能影响，仅保留方法和逻辑分支的插桩，但数据结构不变。
#### 3 生成output/covMap目录，——每个源代码文件根据语法树分析出的方法和分支对应的位置信息的map文件


A Babel plugin that instruments your code with Istanbul coverage.更多使用方法，请查看官方文档。

### Usage

Install it:

```
npm install --save-dev babel-plugin-jscoco
```

Config it in babel：

```
option={
    plugins:[require("babel-plugin-jscoco").default, {
                    filename:fileRelativePath,// 插桩后对应文件显示的文件路径，可定制，方便业务使用。——eg:我们是基于git项目名称的路径
                    exclude: ["**/node_modules/**/*"], // 需要过滤的目录
                }]
    }
```

