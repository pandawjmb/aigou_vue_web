<template>
    <div>
        <el-table
                :data="tableData">
            <el-table-column
                    prop="name"
                    label="手机名称"
                    width="180">
            </el-table-column>
            <el-table-column
                    prop="price"
                    label="价格"
                    width="180">
            </el-table-column>
            <el-table-column
                    prop="stock"
                    label="库存">
            </el-table-column>
        </el-table>
        <el-button @click="reload">刷新</el-button>
    </div>
</template>

<script>
    import {getPhoneList} from '../../api/api.js'
    export default {
        data() {
            return {
                tableData: []
            }
        },
        methods:{
            reload(){
                getPhoneList().then(res=>{
                    this.tableData = res.data
                    this.$message.success('手机列表加载成功')
                }).catch(e=>{
                    this.$message.error('手机列表加载')
                })
            }
        },
        mounted(){
            this.reload()
        }
    }
</script>