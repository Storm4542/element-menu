<template>
    <div>

        <template v-for="submenu in menuData">
            <el-submenu v-if="submenu.childMenu&&submenu.childMenu.length>0" :index="submenu.index">
                <template slot="title">
                    <i :class="submenu.icon"></i>
                    <span>{{submenu.name}}</span>
                </template>
                <!--                普通菜单-->
                <template v-if="submenu.childMenu&&submenu.childMenu.length>0">
                    <template v-if="hasChildMenu(submenu.childMenu)">
                        <g-el-menu :menu-data="submenu.childMenu"></g-el-menu>
                    </template>
                    <template v-else>
                        <el-menu-item v-for="item in submenu.childMenu" :key="item.index" :index="item.index">
                            <i :class="item.icon"></i>
                            <span slot="title">
                                {{item.name}}
                            </span>
                        </el-menu-item>
                    </template>
                </template>
            </el-submenu>
            <el-menu-item :index="submenu.index" v-else>
                <i :class="submenu.icon"></i>
                <span slot="title">{{submenu.name}}</span>
            </el-menu-item>
        </template>

    </div>

</template>

<script>
    export default {
        name: "g-el-menu",
        props: {
            menuData: {
                type: [Object, Array],
                required: true,
            }
        },
        computed: {},
        methods: {
            hasChildMenu(obj) {
                //判断是否有儿子
                let t = false;
                console.log('c', obj);
                obj.forEach(item => {
                    if (item.childMenu && item.childMenu.length > 0) {
                        t = true;
                    }
                });
                return t;
            },
            handleOpen(key, keyPath) {
                console.log(key, keyPath);
            },
            handleClose(key, keyPath) {
                console.log(key, keyPath);
            }
        }
    };
</script>

<style scoped>
    .el-menu-vertical-demo {
        width: 100%;
        height: 100%;
        /*height: 100vh;*/
    }
</style>
