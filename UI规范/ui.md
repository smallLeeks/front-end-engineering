### UI规范(Less) 

#### 品牌色
```
@qysblue-1: color-palette(@qysblue-6, 1);
@qysblue-2: color-palette(@qysblue-6, 2);
@qysblue-3: color-palette(@qysblue-6, 3);
@qysblue-4: color-palette(@qysblue-6, 4);
@qysblue-5: color-palette(@qysblue-6, 5);
@qysblue-6: #015BED;
```

#### 错误 Danger
```
@orangered-1: color-palette(@orangered-6, 1);
@orangered-2: color-palette(@orangered-6, 2);
@orangered-3: color-palette(@orangered-6, 3);
@orangered-4: color-palette(@orangered-6, 4);
@orangered-5: color-palette(@orangered-6, 5);
@orangered-6: #ed521f;
```

#### 提示 Warning
```
@yellow-1: color-palette(@yellow-6, 1);
@yellow-2: color-palette(@yellow-6, 2);
@yellow-3: color-palette(@yellow-6, 3);
@yellow-4: color-palette(@yellow-6, 4);
@yellow-5: color-palette(@yellow-6, 5);
@yellow-6: #F0A128;
```

#### 成功 Success
```
@green-1: color-palette(@green-6, 1);
@green-2: color-palette(@green-6, 2);
@green-3: color-palette(@green-6, 3);
@green-4: color-palette(@green-6, 4);
@green-5: color-palette(@green-6, 5);
@green-6: #2bb353 ;
```

#### 其他系统颜色 - 氰基蓝 Cyanyl blue
```
@cyan-1: color-palette(@cyan-6, 1);
@cyan-2: color-palette(@cyan-6, 2);
@cyan-3: color-palette(@cyan-6, 3);
@cyan-4: color-palette(@cyan-6, 4);
@cyan-5: color-palette(@cyan-6, 5);
@cyan-6: #6BB6C0;
```

#### 薰衣草紫 Lavender Purple
```
@purple-1: color-palette(@purple-6, 1);
@purple-2: color-palette(@purple-6, 2);
@purple-3: color-palette(@purple-6, 3);
@purple-4: color-palette(@purple-6, 4);
@purple-5: color-palette(@purple-6, 5);
@purple-6: #AD96E6;
```

#### 填充 - 常规浅色背景
```
@gray-1: #F7F8FB;
```
#### 边框 - 浅 或者 填充 - 特殊背景/白底hover悬浮
```
@gray-2: #F0F2F7;
```
#### 填充 - 特殊背景
```
@gray-3: #E1E4EB;
```
#### 边框（一般）、填充（浅色图标）、文字（置灰信息/禁用）
```
@gray-4: #CCD0D9;
```
#### 填充（常规图标）、文字（文本说明）
```
@gray-5: #9BA3B0;
```
#### 填充（强调/图标/特殊场景）、文字（次要信息）
```
@gray-6: #9BA3B0;
```
#### 文字 - 次强调/正文标题/文本
```
@gray-7: #4e5969;
```
#### 文字 - 强调/正文标题
```
@gray-8: #1d2129;
```

#### borderSize
```
@border-none: 0;
@border-1: 1px;
@border-2: 2px;
@border-3: 3px;
@border-4: 4px;
@border-5: 5px;
```

#### borderStyle
```
@border-solid: solid;
@border-dashed: dashed;
@border-dotted: dotted;
```

#### size
```
@size-none: 0;
@size-1: 10px;
@size-2: 12px;
@size-3: 13px;
@size-4: 14px;
@size-5: 16px;
@size-6: 18px;
@size-7: 20px;
@size-8: 24px;
```

#### shadow
```
@shadow-none: none;
@shadow-card: 0px 0px 8px rgba(0, 19, 48, 0.08); // 适用场景：白底卡片
@shadow-drawer-right: -2px 0px 12px rgba(0, 19, 48, 0.08); // 适用场景：右侧抽屉
@shadow-table-supernatant: -2px 0px 8px rgba(0, 19, 48, 0.08); // 适用场景：表格右侧浮层
@shadow-menu-up: 0px 2px 4px rgba(0, 19, 48, 0.06); // 适用场景：用于顶部菜单栏及工具栏
@shadow-​popconfirm: 0px 4px 20px rgba(0, 19, 48, 0.12); // 适用场景：气泡卡片
@shadow-modal: 0px 2px 16px rgba(0, 19, 48, 0.12); // 适用场景：弹窗对话框
@shadow-​dropdown: 0px 2px 8px rgba(0, 19, 48, 0.12); // 适用场景：下拉菜单
```

#### opacity
```
@opacity-none: 0;
@opacity-1: 10%;
@opacity-2: 20%;
@opacity-3: 30%;
@opacity-4: 40%;
@opacity-5: 50%;
@opacity-6: 60%;
@opacity-7: 70%;
@opacity-8: 80%;
@opacity-9: 90%;
@opacity-10: 100%;
```

#### fontSize
```
@font-size-title-4: 24px; // 特殊-大（登录页/详情页）
@font-size-title-3: 20px; // 标题-大
@font-size-title-2: 18px; // 特殊-中（抽屉标题）
@font-size-title-1: 16px; // 标题-中（二级页及弹窗标题）
@font-size-body-3: 14px; // 标题-小（小版块/tab标题）
@font-size-body-2: 13px; // 特殊-小（文本标题）
@font-size-body-1: 12px; // 辅助文案加粗
@font-size-special: 10ox; // 特殊字体（不常用）
```

#### fontWeight
```
@font-weight-100: 100;
@font-weight-200: 200;
@font-weight-300: 300; 
@font-weight-400: 400;
@font-weight-500: 500;
@font-weight-600: 600;
@font-weight-700: 700;
@font-weight-800: 800;
@font-weight-900: 900;
```