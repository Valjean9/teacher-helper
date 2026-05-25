<template>
  <div class="app">
    <!-- 顶部导航栏 -->
    <div class="header">
      <h1>📝 教师教案助手</h1>
      <div class="nav">
        <el-button type="primary" plain>教案编辑</el-button>
        <el-button type="primary" plain>资源库</el-button>
        <el-button type="primary" plain>AI助手</el-button>
        <el-button type="primary" plain>教师社群</el-button>
        <el-button type="success" round @click="loginDialogVisible = true">登录 / 注册</el-button>
      </div>
    </div>

    <!-- 中间内容区 -->
    <div class="main">
      <!-- 欢迎横幅 -->
      <div class="hero">
        <h2>让备课更轻松，让教学更高效</h2>
        <p>AI辅助编写教案 | 海量教学资源 | 教师交流社群</p>
        <el-button type="primary" size="large">开始编写教案</el-button>
      </div>

      <!-- 功能卡片区 -->
      <div class="features">
        <div class="card">
          <h3>✏️ 智能教案编辑器</h3>
          <p>在线编辑、导出Word/PDF、打印，一站式完成教案编写</p>
        </div>
        <div class="card">
          <h3>📚 教学资源库</h3>
          <p>教案模板、课程标准、教学案例，随时下载使用</p>
        </div>
        <div class="card">
          <h3>🤖 AI教学助手</h3>
          <p>图转文、智能建议，AI帮你快速生成教案</p>
        </div>
        <div class="card">
          <h3>💬 教师社群</h3>
          <p>与全国教师交流经验，分享教学心得</p>
        </div>
      </div>
    </div>
  </div>
      <!-- 登录弹窗 -->
    <el-dialog v-model="loginDialogVisible" title="登录教案助手" width="400px">
      <el-form :model="loginForm" label-width="80px">
        <el-form-item label="用户名">
          <el-input v-model="loginForm.username" placeholder="请输入用户名" />
        </el-form-item>
        <el-form-item label="密码">
          <el-input v-model="loginForm.password" type="password" placeholder="请输入密码" />
        </el-form-item>
        <el-form-item label="演示说明">
          <span style="color: #999; font-size: 12px;">随便输入用户名和密码即可登录</span>
        </el-form-item>
      </el-form>
      <template #footer>
        <el-button @click="loginDialogVisible = false">取消</el-button>
        <el-button type="primary" @click="handleLogin">登录</el-button>
        <el-button type="success" plain @click="handleRegister">注册</el-button>
      </template>
    </el-dialog>
</template>

<script setup>
import { ref } from 'vue'
import { ElMessage } from 'element-plus'

// 控制登录弹窗是否显示
const loginDialogVisible = ref(false)

// 登录表单数据
const loginForm = ref({
  username: '',
  password: ''
})

// 处理登录
const handleLogin = () => {
  if (loginForm.value.username && loginForm.value.password) {
    ElMessage.success(`欢迎回来，${loginForm.value.username}老师！`)
    loginDialogVisible.value = false
    loginForm.value = { username: '', password: '' }
  } else {
    ElMessage.warning('请输入用户名和密码')
  }
}

// 注册（暂时简单的演示）
const handleRegister = () => {
  ElMessage.info('注册功能开发中，请先使用演示账号：任意用户名和密码')
}
</script>

<style scoped>
.app {
  min-height: 100vh;
  background: #f5f7fa;
}

.header {
  background: white;
  padding: 0 40px;
  height: 70px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
  position: sticky;
  top: 0;
}

.header h1 {
  color: #409EFF;
  font-size: 24px;
}

.nav {
  display: flex;
  gap: 10px;
  align-items: center;
}

.main {
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 20px;
}

.hero {
  background: linear-gradient(135deg, #409EFF 0%, #66b1ff 100%);
  border-radius: 24px;
  padding: 60px 40px;
  text-align: center;
  color: white;
  margin-bottom: 50px;
}

.hero h2 {
  font-size: 36px;
  margin-bottom: 16px;
}

.hero p {
  font-size: 18px;
  margin-bottom: 30px;
  opacity: 0.9;
}

.features {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 24px;
}

.card {
  background: white;
  padding: 28px;
  border-radius: 20px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.05);
  transition: transform 0.2s;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 24px rgba(0,0,0,0.1);
}

.card h3 {
  font-size: 20px;
  margin-bottom: 12px;
  color: #2c3e50;
}

.card p {
  color: #666;
  line-height: 1.6;
}
</style>