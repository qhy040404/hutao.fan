<script setup>
import { ref } from 'vue'

// 页面数据
const features = [
  {
    title: '接入厂商',
    value: '6+'
  },
  {
    title: '独立节点',
    value: '3+'
  },
  {
    title: '订阅价格',
    value: '1元'
  }
]

// 对话框控制
const showDialog = ref(false)

// 合作项目数据
const projects = [
  {
    name: 'Snap Hutao',
    url: 'https://hut.ao/',
    icon: new URL('./assets/snap-hutao-icon.png', import.meta.url).href
  },
  {
    name: 'Yae',
    url: 'https://github.com/HolographicHat/Yae',
    icon: new URL('./assets/yae-icon.png', import.meta.url).href
  },
  {
    name: 'BetterGI',
    url: 'https://bettergi.com/',
    icon: new URL('./assets/bettergi-icon.png', import.meta.url).href
  }
]

// 获取权限跳转
const getPermission = () => {
  window.open('https://afdian.com/item/274f5a7cbe9911efab6552540025c377', '_blank')
}

// 显示合作项目对话框
const showProjects = () => {
  showDialog.value = true
}

// 关闭对话框
const closeDialog = () => {
  showDialog.value = false
}

// 打开项目链接
const openProject = (url) => {
  window.open(url, '_blank')
}
</script>

<template>
  <div class="app">
    <!-- 背景图片 -->
    <div class="background-image"></div>

    <!-- 主要内容区域 -->
    <div class="content-wrapper">
      <!-- 整体内容容器 -->
      <div class="main-container">
        <!-- 标题区域 -->
        <header class="header">
          <img src="./assets/header-logo.png" alt="Logo" class="header-logo" />
          <h1 class="title">Snap Hutao CDN</h1>
        </header>

        <!-- 特色服务展示 -->
        <main class="main-content">
          <div class="features-grid">
            <div
              v-for="feature in features"
              :key="feature.title"
              class="feature-card"
            >
              <div class="feature-value">{{ feature.value }}</div>
              <div class="feature-title">{{ feature.title }}</div>
            </div>
          </div>

          <!-- 按钮区域 -->
          <div class="buttons-section">
            <button class="btn btn-primary" @click="getPermission">
              获取权限
            </button>
            <button class="btn btn-secondary" @click="showProjects">
              合作项目
            </button>
          </div>

          <!-- ICP备案号 -->
          <footer class="icp-footer">
            <a href="https://beian.miit.gov.cn/" target="_blank" class="icp-link">
              蜀ICP备2022025022号
            </a>
          </footer>
        </main>
      </div>
    </div>

    <!-- 合作项目对话框 -->
    <div v-if="showDialog" class="dialog-overlay" @click="closeDialog">
      <div class="dialog" @click.stop>
        <div class="dialog-header">
          <h3>合作项目</h3>
          <button class="close-btn" @click="closeDialog">×</button>
        </div>
        <div class="dialog-content">
          <div
            v-for="project in projects"
            :key="project.name"
            class="project-item"
            @click="openProject(project.url)"
          >
            <img :src="project.icon" :alt="project.name" class="project-icon" />
            <div class="project-name">{{ project.name }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.app {
  position: relative;
  min-height: 100vh;
  overflow-x: hidden;
}

.background-image {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url('./assets/128173691_p0.png');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  z-index: -1;
}

.content-wrapper {
  position: relative;
  z-index: 1;
  padding: 1rem;
  width: 100%;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  min-height: 100vh;
}

.main-container {
  background: rgba(255, 255, 255, 0.4);
  backdrop-filter: blur(30px);
  -webkit-backdrop-filter: blur(30px);
  border: 2px solid rgba(255, 255, 255, 0.5);
  border-radius: 24px;
  padding: 2rem 1.5rem;
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.25);
  width: 100%;
  max-width: 400px;
  margin-right: 0;
  height: calc(100vh - 2rem);
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
}

.header {
  text-align: center;
  margin-bottom: 1rem;
}

.header-logo {
  width: 140px;
  height: auto;
  margin-bottom: 0.8rem;
}

.title {
  font-size: 2.5rem;
  font-weight: 700;
  background: linear-gradient(135deg, #ff4757, #2f3542);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin: 0;
}

.main-content {
  display: flex;
  flex-direction: column;
}

.features-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 0.8rem;
}

.feature-card {
  background: rgba(255, 255, 255, 0.25);
  backdrop-filter: blur(15px);
  -webkit-backdrop-filter: blur(15px);
  border: 1px solid rgba(255, 255, 255, 0.4);
  border-radius: 16px;
  padding: 1rem;
  text-align: center;
  transition: transform 0.3s ease, background 0.3s ease;
}

.feature-card:hover {
  transform: translateY(-3px);
  background: rgba(255, 255, 255, 0.35);
}

.feature-value {
  font-size: 2rem;
  font-weight: 700;
  background: linear-gradient(135deg, #ff4757, #ff6b81);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 0.3rem;
}

.feature-title {
  font-size: 1.1rem;
  font-weight: 600;
  color: #1a1a1a;
  margin-bottom: 0.3rem;
}

.buttons-section {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-top: 1rem;
}

.btn {
  padding: 0.8rem;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  font-size: 1rem;
  font-weight: 500;
  transition: background 0.3s ease, transform 0.3s ease;
}

.btn-primary {
  background: linear-gradient(135deg, #ff4757, #ff6b81);
  color: white;
}

.btn-secondary {
  background: rgba(255, 255, 255, 0.2);
  color: #333;
}

.btn-primary:hover {
  background: linear-gradient(135deg, #ff6b81, #ff4757);
  transform: translateY(-2px);
}

.btn-secondary:hover {
  background: rgba(255, 255, 255, 0.3);
}

.icp-footer {
  margin-top: 1rem;
  text-align: center;
}

.icp-link {
  font-size: 0.9rem;
  color: #666;
  text-decoration: none;
  padding: 0.3rem 0.6rem;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.icp-link:hover {
  background: linear-gradient(135deg, #ff4757, #ff6b81);
  color: white;
  text-decoration: none;
}

.dialog-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  z-index: 1000;
  display: flex;
  justify-content: center;
  align-items: center;
}

.dialog {
  background: white;
  border-radius: 16px;
  padding: 2rem;
  width: 90%;
  max-width: 500px;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.3);
  position: relative;
}

.dialog-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
  padding-bottom: 0.5rem;
}

.dialog-header h3 {
  margin: 0;
  font-size: 1.2rem;
  font-weight: 600;
  color: #c44569;
}

.close-btn {
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  color: #666;
  padding: 0.2rem;
  border-radius: 4px;
  transition: background 0.3s ease;
}

.close-btn:hover {
  background: rgba(0, 0, 0, 0.1);
  color: #333;
}

.dialog-content {
  max-height: 60vh;
  overflow-y: auto;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 1rem;
}

.project-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0.8rem;
  border-radius: 12px;
  cursor: pointer;
  transition: background 0.3s ease;
  position: relative;
}

.project-item:hover {
  background: rgba(0, 0, 0, 0.05);
}

.project-icon {
  width: 56px;
  height: 56px;
  border-radius: 50%;
  margin-bottom: 0.6rem;
}

.project-name {
  font-size: 0.9rem;
  font-weight: 600;
  color: #333;
  margin-bottom: 0.3rem;
  text-align: center;
}

@media (max-width: 768px) {
  .content-wrapper {
    padding: 0.5rem;
    justify-content: center;
  }

  .main-container {
    padding: 1rem;
    max-width: 300px;
  }

  .header-logo {
    width: 110px;
  }

  .title {
    font-size: 1.8rem;
  }

  .features-grid {
    gap: 0.6rem;
  }

  .header {
    margin-bottom: 0.8rem;
  }

  .feature-card {
    padding: 0.8rem;
  }

  .feature-value {
    font-size: 2rem;
  }

  .feature-title {
    font-size: 1.2rem;
  }

  .btn {
    font-size: 0.9rem;
    padding: 0.6rem;
  }

  .dialog {
    padding: 1.5rem;
  }

  .dialog-content {
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
    gap: 0.8rem;
  }

  .project-item {
    padding: 0.6rem;
  }

  .project-icon {
    width: 48px;
    height: 48px;
    margin-bottom: 0.5rem;
  }

  .project-name {
    font-size: 0.8rem;
  }
}
</style>
