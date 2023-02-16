## electron+vite+vue3

1. `node >= 14.18.0`

### 目标

实现 `electron + vite + vue3` 打包成一个 `window` 和 `mac` 的安装包

[参考项目地址，分支(electron-node-proxy)](https://github.com/nimengyijunduo/vue-program-template)

1. 创建一个 `vue3 + vite` 项目，参考 `vue` 官方文档搭建

2. `$ pnpm add electron electron-builder electron-devtools-installer vite-plugin-electron -D`

`electron-builder`  打包工具
`electron-devtools-installer`  electron开发工具
`vite-plugin-electron`  vite的electron库

3. 根目录创建 `electron` 目录，包含主进程和预加载文件




