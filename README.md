# ts-vue-practice

```
webpack@3.6.0 ts-loader@3.5.0(最新ts-loader需要webpack@4+支持)
```
1、安装ts
```
npm install --save typescript ts-loader@3.5.0
```
2、配置ts
```
# webpack.base.conf.js
1、resolve >  extensions: ['.js', '.vue', '.json', '.ts'],//添加.ts
2、rules > {
              test: /\.tsx?$/,
              loader: 'ts-loader',
              exclude: /node_modules/,
              options: {
                appendTsSuffixTo: [/\.vue$/],
              }
            }
3、根目录下新建tsconfig.json
{
  "include": ["src/**/*"],
  "exclude": ["node_modules"],
  "compilerOptions": {
    "allowSyntheticDefaultImports": true,
    "experimentalDecorators": true,
    "allowJs": true,
    "module": "esnext",
    "target": "es5",
    "moduleResolution": "node",
    "isolatedModules": true,
    "lib": ["dom", "es5", "es6", "es7", "es2015.promise"],
    "sourceMap": true,
    "pretty": true
  }
}
4、src目录下新建vue-shim.d.ts
declare module "*.vue" {
  import Vue from "vue";
  export default Vue;
}
```
3、改后缀
```
# /test/unit/jest.conf.js
collectCoverageFrom: [
  'src/**/*.{js,vue}',
   '!src/main.ts',
   '!src/router/index.ts',
   '!**/node_modules/**'
 ]
 # webpack.base.conf.js
 entry > app: './src/main.ts'
 # /src目录下
 1、router/index.ts
 需要写全.vue后缀(不写全控制台没报错，不过ws会有错误提示)
 2、main.ts
```
参考：https://www.jianshu.com/p/55a23872b39b
