## 介绍

此项目基于 element-UI 2.15.13。

包名为：element2-nmtuan

源码仓库：https://github.com/NMTuan/element

## 修改内容

cascader 级联选择器增加配置项：sortChecked。

> 多选模式下，当 checkStrictly 和 sortChecked 同时为 true，勾选的数据会按照勾选顺序显示。 仅适配了 emitPath 配置项，其它未处理。

具体修改思路可参考：[让 Cascader 按选择顺序显示 (muyi.dev)](https://www.muyi.dev/posts/20230603)

## 使用方式

```bash
# 移除原有 element-ui
yarn remove element-ui
# 引入当前包
yarn add element2-nmtuan
```

然后修改项目中各种 `import x from 'element-ui'` 为 `element2-nmtuan`

最后在 `el-cascader` 的配置项 `props` 中，增加 'sortChecked: true', 如：

```vue
<template>
	<el-cascader 
         v-model="data" 
         :props="cascaderProps"
         :options="options"
     ></el-cascader>
</template>
<script>
export default {
    data(){
        return {
            data: [],
            options: [],
            // 级联选择器的配置
            cascaderProps: {
                checkStrictly: true, // 解除子父节点关联
                multiple: true, // 多选
                sortChecked: true // 按选中顺序显示
            }          
        }
    }
}
</script>
```

