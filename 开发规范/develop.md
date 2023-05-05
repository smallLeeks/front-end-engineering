### 开发规范

#### 组件命名规范
1. `components` 下的组件命名规范遵循大驼峰命名规范
eg: components/AboutCard/index.vue

#### 目录命名规范

1. `pages` 下的文件命名规范：遵循小驼峰命名规范
eg: pages/personCenter/index.vue

#### css 命名规范
1. BEM规范

#### 代码注释规范
1. 行内注释：//
2. 函数注释
``` eg
/**
 * @description
 * @param {string} color
 * @returns {*}
 */
```
3. 接口注释
```
/**
 * @description
 * @param page
 * @param limit
 * @param username
 * @returns {<PageRes<AclUser.ResAclUserList>>}
 * @docs https://xxxx
 */
```

#### 接口书写规范
接口全部卸载 `api` 目录下面，按照功能划分，分为不同的目录

接口书写规范

统一使用类方法，内部方法定义每个接口，最后统一 `export`，接口使用到的类型全部定义在同级目录的 `types/index.ts` 文件中

所有的 `export` 的类接口方法都在 `api/index.ts` 中统一导出