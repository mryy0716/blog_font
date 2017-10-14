<template>
 
    <nav>

        <el-menu theme="dark" :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="Select">
     
    <el-menu-item index="1"><h2>个人博客</h2></el-menu-item>

    <el-submenu v-for="(i,index) in datalist" :index="i.onedata.id" >
       
        <template slot="title">{{i.onedata.cnname}}</template>
<el-menu-item v-for="(j,index2) in i.twodata" :index="j.id">{{j.cnname}}</el-menu-item>

</el-submenu>
</el-menu>
</nav>

</template>

<script>
    import { mapState, mapActions } from "vuex"
    import action_type from "../store/action_type"
    export default {
        name: 'header',
        data() {
            return {
                activeIndex: '1',
            };
        },
        computed: {
            ...mapState({
                datalist: (state) => state.headData
            })
        },
        methods: {
            ...mapActions({
                changeList: action_type.HEADCHANGEDATA.actions,
                // 二级分类点击后改变面包屑数组
                headbreadList: action_type.HEADBREADDATA.actions
            }),
            Select(key, keyPath) {
                this.changeList(key)
                this.datalist.forEach(function(i) {
                    i.twodata.forEach(function(j) {
                        if (j.id == key) {
                            var arr = [{
                                cnname: i.onedata.cnname,
                                oneId: i.onedata.id,
                                twoId: null
                            }, {
                                cnname: j.cnname,
                                oneId: j.parent_id,
                                twoId: j.id
                            }]
                            this.headbreadList(arr)
                        }
                    }.bind(this))
                }, this);

            }
        }
    }
</script>

<style scoped>
    .index {
        width: 1000px;
        margin: 0 auto;
    }
    
    .breadCrumb {
        height: 40px;
        line-height: 40px;
        padding-left: 20px;
    }
    
    .el-row {
        margin-bottom: 20px;
        &:last-child {
            margin-bottom: 0;
        }
    }
    
    .el-col {
        border-radius: 4px;
    }
    
    .grid-content {
        border-radius: 4px;
        min-height: 36px;
    }
    
    
</style>