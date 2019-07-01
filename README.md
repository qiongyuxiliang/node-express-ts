1、全局安装：
npm install -g npm
npm install -g typescript
npm install -g tslint
--------------------- 

2、程序配置
/src/app.ts // 程序入口文件
.npmrc // 项目 npm 配置文件，可针对项目单独设置 npm 的配置
package.json // 项目模块描述文件
tsconfig.json // typescript 配置文件
tslint.json // tslint 配置文件
--------------------- 

3、tsconfig.json配置
如果一个目录下存在存在 tsconfig.json 文件，那么就意味着这个目录是 typescipt 项目的根目录。tsconfig.json 定义了用来编译这个项目的根目录及编译选项。让我们一起来看看其中的一些关键配置项：

"target": "es6" // 指定 EECMAScript 的目标版本, 这里我们采用 es6
"module": "commonjs" // 指定编译生成哪个模块的系统代码，考虑到兼容性，这里我们设置成 commonjs
"moduleResolution": "node" // 决定如何处理模块。设置为 node
"outDir": "dist" // 编译输出目录，即 .ts 文件编译成 .js 文件后的输出目录。这里设置为根目录下的 /dist 目录
"baseUrl": "./" // 定义 ts 项目的根目录，设置 paths 前必须设置 baseUrl，paths中设置的路径是基于根目录来的
"paths": {"*": ["node_modules/*", "src/types/*"], "@/*": ["src/*"]} // 定义路径别名,即当我们通过路径引入一个模块时，可以使用别名来进行引入，这里第一个 * 设置是为了引入第三方模块; 第二个 '@/*' 则是为了直接快捷的导入 /src 下的模块。
"include": ["src/**/*"] // 需要编译的 ts 文件，这里设置为 src 目录下的所有文件
--------------------- 
4、tslint.json
tslint 配置文件，用于检查代码是否符合设置的代码规范，不符合将会提示对应错误。
--------------------- 

5、解决npm node-ts在windows上命令错误

npm install -g cross-env
然后，代码修改,在脚本命令前加上cross-env

  "scripts": {
    "build": "cross-env NODE_ENV=production webpack --config build/webpack.config.js"
  }
  "scripts": {
    "test": "cross-env ts-node index.ts ./api.json"
  }
--------------------- 

