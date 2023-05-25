<template>
    <div style="width: 100vw;height: 100vh;overflow: hidden;display: flex">
        <div style="width: 30vw;height: 100vh">
            <div style="text-align: center;margin: 0 20px">
                <div style="margin-top: 150px">
                    <div style="font-size: 25px">登录</div>
                    <div style="font-size: 14px;color: grey">在进入系统之前请先输入用户名或密码进行登录</div>
                </div>
                <div style="margin-top: 30px">
                    <el-input v-model="form.username" type="text" placeholder="用户名/邮箱">
                        <template #prefix>
                            <el-icon><User/></el-icon>
                        </template>
                    </el-input>
                </div>
                <div style="margin-top: 30px">
                    <el-input v-model="form.password" type="password" placeholder="密码">
                        <template #prefix>
                            <el-icon><Key/></el-icon>
                        </template>
                    </el-input>
                </div>
                <div style="margin-top: 30px">
                    <el-button @click="login()" type="primary">登录</el-button>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import {User} from '@element-plus/icons-vue'
import {Key} from '@element-plus/icons-vue'
import {reactive} from "vue";
import {ElMessage} from "element-plus";
import {post} from "@/net";
import router from "@/router";

const form = reactive({
    username: '',
    password: ''
})

const login = () =>{
    if(!form.username || !form.password){
        ElMessage.warning('请填写用户名和密码')
    }else{
        post('/api/auth/login',{
            username: form.username,
            password: form.password
        },(message) => {
            ElMessage.success(message)
            router.push('/index')
        })
    }
}
</script>

<style scoped>

</style>