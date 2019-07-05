<template>
    <div class = "sidebar">
        <div class = "mainslide">
            <el-row class = "tac">
                <el-col :span = "24">
                    <el-menu
                        default-active = "2"
                        class = "el-menu-vertical-demo"
                        @open = "handleOpen"
                        @close = "handleClose"
                        background-color = "#545c64"
                        text-color = "#fff"
                        active-text-color = "#ffd04b"
                        style = "text-align: left">
                        <el-submenu v-for = "(child, index) in currentNavItems" index = "1">
                            <template slot = "title">
                                <i class = "el-icon-location"></i>
                                <span>{{child.title}}</span>
                            </template>
                            <el-menu-item-group>
                                <el-menu-item v-for = "item in child.subs" index = "1-1">
                                    <a :href = "'#'+item.index" class = "slideLink">{{item.title}}</a></el-menu-item>
                            </el-menu-item-group>
                        </el-submenu>
                    </el-menu>
                </el-col>
            </el-row>
        </div>
    </div>
</template>
<script>
    export default {
        name: 'v-sidebar',
        data(){
            return {
                isClicked: false,
                iconData: {metas: ''},
                systems: '',
                items: '',
                value: '',
                input2: '',
                navData: '',
                currentNavItems: [],
                isHover: false
            }
        },
        methods: {
            sliderHover(){
                this.isClicked = false
            },
            handleOpen(key, keyPath){
                console.log(key, keyPath);
            },
            handleClose(key, keyPath){
                console.log(key, keyPath);
            }
        },
        created(){
            // 从sessionStorage得到menuData
            this.currentNavItems = JSON.parse(sessionStorage.getItem('menuData'));
            console.log(this.currentNavItems);
        }
    }
</script>
<style scoped lang = "scss" type = "text/scss">
    .sidebar {
        height           : 100%;
        display          : block;
        position         : fixed;
        min-width        : 200px;
        left             : 0;
        top              : 61px;
        background-color : #545c64;
        overflow         : hidden;
    }
    .sidebar:hover {
        overflow : scroll;
    }
    .slideLink {
        color           : white;
        text-decoration : none;
    }
</style>
