<template>
    <div class="login-container">
        <el-card class="login-card">
            <h2 class="login-title">登录</h2>
            <el-form label-width="80px" class="login-form" :rules="rules" :model="loginForm" ref="formRef">
                <el-form-item label="用户名" prop="username">
                    <el-input v-model="loginForm.username" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="密码" prop="password">
                    <el-input v-model="loginForm.password" autocomplete="off" :validate-event="false"></el-input>
                </el-form-item>
                <el-form-item>
                    <el-button type="primary" @click="submit">登录</el-button>
                </el-form-item>
            </el-form>
        </el-card>
    </div>
</template>

<script lang="ts" setup>
import { reactive, ref, watch } from 'vue'
import type { FormInstance } from 'element-plus'


const loginForm = ref({
    username: '',
    password: ''
})

const rules = ref({
    username: [
        { required: true, message: '请输入用户名', trigger: 'blur' }
    ],
    password: [
        { required: true, message: '请输入密码', trigger: 'blur' }
    ]
})

const formRef = ref<FormInstance>()

const submit = () => {
    formRef.value?.validate((valid) => {
        if (valid) {
            alert("submit")
        }
        else {
            console.log("error submit")
        }
    })
}

</script>

<style scoped>
.login-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f2f2f2;
}

.login-card {
    width: 400px;
    padding: 20px;
}

.login-title {
    text-align: center;
    margin-bottom: 20px;
}

.login-form {
    width: 100%;
}
</style>