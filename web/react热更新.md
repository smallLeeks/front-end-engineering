### react 热更新

#### HRM（HOt Module Replacement）

`webpack` 自带的功能，通过 `module.hot.accept` 实现。当文件改动重新编译时，HRM 注册的回调执行，刷新浏览器

1、HRM client 负责待打开 `websocket`，连接 `webpack-dev-server`
2、入口调用 `module.hot.accept()`
3、`webpack-dev-server` 监听文件变化，保存时自动重新编译
4、重新编译后，发送消息通知 `client`，通知哪些文件重新编译（控制台日志可以看到冒泡到根组件）
5、`client` 会根据重新编译的文件路径来执行 `module.hot.accept()` 的回调函数

#### react-hot-loader

[地址链接](https://www.npmjs.com/package/react-hot-loader)

使用一个 `proxy Component` 包裹你的组件代码，有自己的状态管理机制，修改文件后，状态保留，不会重新刷新

1、`npm i react-hot-loader -D`

2、`.babelrc` 配置文件
```
{
    plugins: ['react-hot-loader/babel']
}
```

3、`webpack.config.dev.js` 配置文件
```
entry: ['react-hot-loader/patch']
```

4、需要包裹的根组件 react-hot-loader@4.x
```
import { hot } from 'react-hot-loader';

export default hot(module)(组件名)
```

目前存在的问题
1、render => return 中样式和文案更改可以热更新，但 state 数据更改后无法热更新，需要重新刷新浏览器

#### react-refresh

[地址链接](https://www.npmjs.com/package/@pmmmwh/react-refresh-webpack-plugin?activeTab=readme)

目前对 `react`，`react-dom`，`webpack` 等版本要求较高

1、`npm i @pmmmwh/react-refresh-webpack-plugin -D`

2、`webpack-dev-server` 配置文件
```
const ReactRefreshWebpackPlugin = require('@pmmmwh/react-refresh-webpack-plugin');
const ReactRefreshTypeScript = require('react-refresh-typescript');

modules.exports = {
    module: {
        {
                /** 指定loader加载的规则 */
                test: /\.(js|jsx|ts|tsx)$/,
                /** 包含的文件 */
                include: path.join(__dirname, '../src'),
                /** 排除的文件 */
                exclude: /node_modules/,
                /** 要使用的loader简写版 */
                use: [
                    {
                        loader: 'thread-loader',
                        options: WorkerPool,
                    },
                    loader: 'babel-loader',
                    {
                        loader: 'ts-loader',
                        options: {
                            /**
                             * 关闭类型检查，即只进行转译
                             * 类型检查交给 fork-ts-checker-webpack-plugin 在别的的线程中做
                             * transpileOnly: true
                             * 如果设置了 happyPackMode 为 true
                             * 会隐式的设置 transpileOnly: true
                             */
                            happyPackMode: true,
                            plugins: [ReactRefreshTypeScript()],
                        },
                    },
                ],
            },
    }
    plugins: [new ReactRefreshPlugin()]
}
```

目前存在的问题
1、oss 项目对应版本升至要求的版本，但是项目中的 class 组件修改后无法热更新