<template>
    <div id="app">
        <el-row class="tac">
            <el-col :span="12">
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
            </el-col>
        </el-row>
    </div>
</template>

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

<style>
    #app {
    }
</style>
