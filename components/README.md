# 组件说明

## TabBar 底部导航栏

### 介绍

`TabBar` 组件是一个底部导航栏，用于在不同页面之间进行切换。

### 引入

```js
import TabBar from '@/components/TabBar.vue';

export default {
  components: {
    TabBar
  }
}
```

### 代码演示

#### 基础用法

```html
<template>
  <div>
    <TabBar :active="activePage" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      activePage: 'home'
    };
  }
};
</script>
```

### API

#### Props

| 参数 | 说明 | 类型 | 默认值 |
| --- | --- | --- | --- |
| active | 当前激活的标签名 | String | 'home' |

#### 可选值

| 值 | 说明 |
| --- | --- |
| home | 首页标签 |
| orders | 订单标签 |
| my | 我的标签 |

#### 方法

| 方法名 | 说明 | 参数 |
| --- | --- | --- |
| goToPage | 跳转到指定页面 | page: String |