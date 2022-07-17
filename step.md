# 1.shining3d-ui库搭建

## 1、安装pnpm

```
brew install pnpm
```

## 2、创建项目

### 2.1、建立shining-ui

### 2.2、建立readme文件

切换到shining-ui文件常见readme文件

### 2.3、初始化

#### 2.3.1 初始化项目目录。

```js
pnpm init # 初始化package.json配置文件 私有库
```

#### 2.3.2 打开安装目录权限

使用 pnpm 必须要建立 .npmrc 文件， shamefully-hoist = true ，否则安装的模块无法放置 到 node_modules 目录下

```
1、创建.npmrc文件
2、写入 
	shamefully-hoist = true 
```

## 3、安装项目依赖

```
pnpm install vue typescript -D # 全局下添加依赖
```

## 4、初始化ts配置项

### 4.1、创建tsconfig.json文件

```js
npx tsc init
```

### 4.2、tsconfig配置内容如下

```js
{
  "compilerOptions": {
    "module": "ESNext", // 打包模块类型ESNext
    "declaration": false, // 默认不要声明文件 
    "noImplicitAny": true, // 支持类型不标注可以默认any
    "removeComments": true, // 删除注释
    "moduleResolution": "node", // 按照node模块来解析
    "esModuleInterop": true, // 支持es6,commonjs模块
    "jsx": "preserve", // jsx 不转
    "noLib": false, // 不处理类库
    "target": "es6", // 遵循es6版本
    "sourceMap": true,
    "lib": [ // 编译时用的库
      "ESNext",
      "DOM"
    ],
    "allowSyntheticDefaultImports": true, // 允许没有导出的模块中导入
    "experimentalDecorators": true, // 装饰器语法
    "forceConsistentCasingInFileNames": true, // 强制区分大小写
    "resolveJsonModule": true, // 解析json模块
    "strict": true, // 是否启动严格模式
    "skipLibCheck": true // 跳过类库检测
  },
  "exclude": [ // 排除掉哪些类库
    "node_modules",
    "**/__tests__",
    "dist/**"
  ]
}
```

## 5、创建组件测试环境

#### 5.1、创建测试环境分包

```js
//根目录执行
pnpm create vite play --template vue-ts 
```

#### 5.2、提供typescript声明文件 **typings/vue-shim.d.ts** 识别vue模块

```
1、根目录下创建typings文件
2、移植playground目录下的vue-shim.d.ts
```

## 6、创建组件开发模块

初始化packages部分的模块

```js
cd components && pnpm init # @zi-shui/components
cd utils && pnpm init # @zi-shui/utils
cd theme-chalk && pnpm init # @zi-shui/theme-chalk
```

