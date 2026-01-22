<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

interface Service {
  icon: string
  title: string
  description: string
  features: string[]
}

const services = ref<Service[]>([
  {
    icon: '🌐',
    title: '网站开发',
    description: '打造高性能、响应式的现代化网站',
    features: ['企业官网', '电商平台', '管理系统', 'H5页面']
  },
  {
    icon: '📱',
    title: 'APP开发',
    description: '原生与跨平台移动应用开发',
    features: ['iOS应用', 'Android应用', 'React Native', 'Flutter']
  },
  {
    icon: '💼',
    title: '小程序开发',
    description: '全平台小程序定制开发服务',
    features: ['微信小程序', '支付宝小程序', '抖音小程序', '百度小程序']
  },
  {
    icon: '⚙️',
    title: '功能定制',
    description: '根据需求提供专业的定制化解决方案',
    features: ['API接口', '数据分析', '支付集成', '第三方对接']
  }
])

const stats = ref([
  { number: '100+', label: '完成项目' },
  { number: '50+', label: '合作客户' },
  { number: '5年', label: '行业经验' },
  { number: '98%', label: '客户满意度' }
])

const navigateToContact = () => {
  router.push('/contact')
}

const navigateToPortfolio = () => {
  router.push('/portfolio')
}
</script>

<template>
  <div class="home">
    <!-- 英雄区域 -->
    <section class="hero">
      <div class="container">
        <div class="hero-content fade-in">
          <h1 class="hero-title">
            专业的技术团队<br />
            为您打造卓越的数字产品
          </h1>
          <p class="hero-description">
            我们专注于网站、APP、小程序等数字产品的定制开发<br />
            用技术驱动创新，用专业成就梦想
          </p>
          <div class="hero-actions">
            <button class="btn btn-primary" @click="navigateToContact">
              立即咨询
            </button>
            <button class="btn btn-outline" @click="navigateToPortfolio">
              查看案例
            </button>
          </div>
        </div>

        <div class="hero-visual">
          <div class="floating-card card-1">
            <div class="card-icon">💻</div>
            <div class="card-text">Web开发</div>
          </div>
          <div class="floating-card card-2">
            <div class="card-icon">📱</div>
            <div class="card-text">移动应用</div>
          </div>
          <div class="floating-card card-3">
            <div class="card-icon">🚀</div>
            <div class="card-text">快速交付</div>
          </div>
        </div>
      </div>
    </section>

    <!-- 数据统计 -->
    <section class="stats-section">
      <div class="container">
        <div class="stats-grid">
          <div v-for="(stat, index) in stats" :key="index" class="stat-item scale-in">
            <div class="stat-number">{{ stat.number }}</div>
            <div class="stat-label">{{ stat.label }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- 服务介绍 -->
    <section class="services-section section">
      <div class="container">
        <h2 class="section-title">我们的服务</h2>
        <p class="section-subtitle">
          提供全方位的数字化解决方案，助力企业数字化转型
        </p>

        <div class="services-grid">
          <div
            v-for="(service, index) in services"
            :key="index"
            class="service-card card"
          >
            <div class="service-icon">{{ service.icon }}</div>
            <h3 class="service-title">{{ service.title }}</h3>
            <p class="service-description">{{ service.description }}</p>
            <ul class="service-features">
              <li v-for="(feature, idx) in service.features" :key="idx">
                <span class="feature-dot">•</span>
                {{ feature }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- 工作流程 -->
    <section class="process-section section">
      <div class="container">
        <h2 class="section-title">合作流程</h2>
        <p class="section-subtitle">
          简单高效的合作流程，让项目开发更加顺畅
        </p>

        <div class="process-timeline">
          <div class="process-item">
            <div class="process-number">01</div>
            <h3 class="process-title">需求沟通</h3>
            <p class="process-description">深入了解您的需求和目标</p>
          </div>
          <div class="process-connector"></div>

          <div class="process-item">
            <div class="process-number">02</div>
            <h3 class="process-title">方案设计</h3>
            <p class="process-description">制定详细的技术方案和设计稿</p>
          </div>
          <div class="process-connector"></div>

          <div class="process-item">
            <div class="process-number">03</div>
            <h3 class="process-title">开发实施</h3>
            <p class="process-description">按照计划进行开发和测试</p>
          </div>
          <div class="process-connector"></div>

          <div class="process-item">
            <div class="process-number">04</div>
            <h3 class="process-title">交付上线</h3>
            <p class="process-description">完成交付并提供后续支持</p>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA区域 -->
    <section class="cta-section">
      <div class="container">
        <div class="cta-content">
          <h2 class="cta-title">准备开始您的项目了吗？</h2>
          <p class="cta-description">
            联系我们，让我们一起将您的想法变为现实
          </p>
          <button class="btn btn-primary" @click="navigateToContact">
            免费咨询
          </button>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.home {
  padding-top: 70px;
}

/* 英雄区域 */
.hero {
  min-height: calc(100vh - 70px);
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
  background: linear-gradient(135deg, var(--bg-primary) 0%, var(--bg-secondary) 100%);
}

.hero .container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
}

.hero-content {
  z-index: 1;
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 800;
  line-height: 1.2;
  margin-bottom: 1.5rem;
  color: var(--text-primary);
}

.hero-description {
  font-size: 1.25rem;
  color: var(--text-secondary);
  margin-bottom: 2.5rem;
  line-height: 1.8;
}

.hero-actions {
  display: flex;
  gap: 1rem;
}

.hero-visual {
  position: relative;
  height: 500px;
}

.floating-card {
  position: absolute;
  background: var(--bg-card);
  border-radius: 16px;
  padding: 1.5rem 2rem;
  box-shadow: var(--shadow-xl);
  display: flex;
  align-items: center;
  gap: 1rem;
  border: 1px solid var(--border-color);
  animation: float 3s ease-in-out infinite;
}

.floating-card.card-1 {
  top: 20%;
  left: 10%;
  animation-delay: 0s;
}

.floating-card.card-2 {
  top: 50%;
  right: 10%;
  animation-delay: 1s;
}

.floating-card.card-3 {
  bottom: 20%;
  left: 20%;
  animation-delay: 2s;
}

.card-icon {
  font-size: 2rem;
}

.card-text {
  font-weight: 600;
  color: var(--text-primary);
}

@keyframes float {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-20px);
  }
}

/* 数据统计 */
.stats-section {
  padding: 4rem 0;
  background: var(--bg-secondary);
  border-top: 1px solid var(--border-color);
  border-bottom: 1px solid var(--border-color);
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 2rem;
}

.stat-item {
  text-align: center;
}

.stat-number {
  font-size: 3rem;
  font-weight: 800;
  background: var(--accent-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 0.5rem;
}

.stat-label {
  font-size: 1rem;
  color: var(--text-secondary);
}

/* 服务介绍 */
.services-section {
  background: var(--bg-primary);
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
}

.service-card {
  text-align: center;
}

.service-icon {
  font-size: 3.5rem;
  margin-bottom: 1.5rem;
}

.service-title {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 1rem;
}

.service-description {
  color: var(--text-secondary);
  margin-bottom: 1.5rem;
  line-height: 1.6;
}

.service-features {
  list-style: none;
  text-align: left;
}

.service-features li {
  color: var(--text-secondary);
  margin-bottom: 0.5rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.feature-dot {
  color: var(--accent-primary);
  font-weight: bold;
}

/* 工作流程 */
.process-section {
  background: var(--bg-secondary);
}

.process-timeline {
  display: flex;
  align-items: center;
  justify-content: space-between;
  max-width: 1000px;
  margin: 0 auto;
}

.process-item {
  flex: 1;
  text-align: center;
}

.process-number {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  background: var(--accent-gradient);
  color: white;
  font-size: 1.5rem;
  font-weight: 700;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.5rem;
  box-shadow: var(--shadow-lg);
}

.process-title {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 0.5rem;
}

.process-description {
  color: var(--text-secondary);
  font-size: 0.95rem;
}

.process-connector {
  width: 60px;
  height: 2px;
  background: var(--border-color);
  margin: 0 1rem;
  margin-bottom: 80px;
}

/* CTA区域 */
.cta-section {
  padding: 6rem 0;
  background: var(--accent-gradient);
  text-align: center;
}

.cta-content {
  max-width: 700px;
  margin: 0 auto;
}

.cta-title {
  font-size: 2.5rem;
  font-weight: 700;
  color: white;
  margin-bottom: 1rem;
}

.cta-description {
  font-size: 1.25rem;
  color: rgba(255, 255, 255, 0.9);
  margin-bottom: 2rem;
}

.cta-section .btn-primary {
  background: white;
  color: var(--accent-primary);
}

.cta-section .btn-primary:hover {
  transform: translateY(-2px) scale(1.05);
}

/* 响应式 */
@media (max-width: 968px) {
  .hero .container {
    grid-template-columns: 1fr;
  }

  .hero-visual {
    display: none;
  }

  .hero-title {
    font-size: 2.5rem;
  }

  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .process-timeline {
    flex-direction: column;
  }

  .process-connector {
    width: 2px;
    height: 40px;
    margin: 1rem 0;
  }
}

@media (max-width: 640px) {
  .hero-title {
    font-size: 2rem;
  }

  .hero-description {
    font-size: 1rem;
  }

  .hero-actions {
    flex-direction: column;
  }

  .hero-actions .btn {
    width: 100%;
  }

  .stats-grid {
    grid-template-columns: 1fr;
  }

  .stat-number {
    font-size: 2.5rem;
  }

  .cta-title {
    font-size: 1.75rem;
  }

  .cta-description {
    font-size: 1rem;
  }
}
</style>
