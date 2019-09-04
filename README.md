# element-menu

因为`element`的`menu`不支持`JSON`构造，因此根据项目要求封装一下。

因为使用的递归组件，所以支持无限分级。

**注意：不支持分组模式**

首先引入，然后就可以使用了。

示例

```javascript
 <el-menu
           default-active="2"
           class="el-menu-vertical-demo"
           @open="handleOpen"
           @close="handleClose"
            background-color="#545c64"
            text-color="#fff"
            active-text-color="#ffd04b">
          <g-menu :menu-data="menuList.menu"></g-menu>
</el-menu>
```



```javascript
<script>
    import GMenu from './components/menu';

    export default {
        name: 'app',
        components: {
            GMenu
        },
        data() {
            return {
                menuList: {
                    "des": "此文件模拟从后端传来的菜单",
                    "menu": [
                        {
                            "index": "用户管理",
                            "name": "用户管理",
                            "icon": "el-icon-setting",
                            "childMenu": [
                                {
                                    "index": "vue应用",
                                    "icon": "el-icon-setting",
                                    "name": "vue应用",

                                },
                                {
                                    "index": "router应用",
                                    "icon": "el-icon-setting",
                                    "name": "router应用",
                                    "childMenu": [
                                        {
                                            "index": "vue2应用",
                                            "icon": "el-icon-setting",
                                            "name": "vue应用"
                                        },
                                        {
                                            "index": "router2应用",
                                            "icon": "el-icon-setting",
                                            "name": "router应用",

                                        }
                                    ]
                                }
                            ]
                        },
                        {
                            "index": "java应用",
                            "name": "java应用",
                            "icon": "el-icon-setting"
                        },
                        {
                            "index": "c#应用",
                            "name": "c#应用",
                            "icon": "el-icon-setting"
                        }
                    ]
                }

            };
        },
        methods: {
            handleOpen(key, keyPath) {
                console.log(key, keyPath);
            },
            handleClose(key, keyPath) {
                console.log(key, keyPath);
            }
        }
    };
</script>
```

`childMenu`可以无限增加，依照上面`menuList.menu`中的格式写即可。

文件位于 `src/components/menu.vue`

使用示例位于` src/App.vue`

项目中必须已有`ElementUI`才可正常使用