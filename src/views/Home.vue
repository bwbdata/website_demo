<script setup lang="ts">
import { ref, onMounted } from 'vue'
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
  { number: '100+', label: '完成项目', suffix: '' },
  { number: '50+', label: '合作客户', suffix: '' },
  { number: '5', label: '行业经验', suffix: '年' },
  { number: '98', label: '客户满意度', suffix: '%' }
])

const techStack = ref([
  'Vue.js', 'React', 'TypeScript', 'Node.js',
  'Flutter', 'React Native', 'Python', 'Java',
  'MySQL', 'MongoDB', 'Redis', 'Docker'
])

const navigateToContact = () => {
  router.push('/contact')
}

const navigateToPortfolio = () => {
  router.push('/portfolio')
}

// 数字滚动动画
const animatedStats = ref(stats.value.map(() => 0))

onMounted(() => {
  // 数字动画
  stats.value.forEach((stat, index) => {
    const target = parseInt(stat.number)
    const duration = 2000
    const steps = 60
    const increment = target / steps
    let current = 0

    const timer = setInterval(() => {
      current += increment
      if (current >= target) {
        animatedStats.value[index] = target
        clearInterval(timer)
      } else {
        animatedStats.value[index] = Math.floor(current)
      }
    }, duration / steps)
  })
})
</script>

<template>
  <div class="home">
    <!-- 背景动画 -->
    <div class="bg-animation">
      <div class="grid-lines"></div>
      <div class="floating-particles">
        <div v-for="i in 20" :key="i" class="particle" :style="{
          left: Math.random() * 100 + '%',
          top: Math.random() * 100 + '%',
          animationDelay: Math.random() * 5 + 's',
          animationDuration: (5 + Math.random() * 10) + 's'
        }"></div>
      </div>
    </div>

    <!-- 英雄区域 -->
    <section class="hero">
      <div class="container">
        <div class="hero-content fade-in">
          <div class="hero-badge">
            <span class="badge-icon">⚡</span>
            <span class="badge-text">大厂精英 · 专业团队</span>
          </div>
          <h1 class="hero-title">
            <span class="title-line">打造极致的</span>
            <span class="title-highlight">数字化体验</span>
          </h1>
          <p class="hero-description">
            汇聚阿里、字节、腾讯等大厂精英<br />
            为您提供专业的网站、APP、小程序定制开发服务
          </p>
          <div class="hero-actions">
            <button class="btn btn-primary btn-glow" @click="navigateToContact">
              <span>立即咨询</span>
              <span class="btn-arrow">→</span>
            </button>
            <button class="btn btn-outline" @click="navigateToPortfolio">
              查看案例
            </button>
          </div>

          <!-- 技术标签云 -->
          <div class="tech-tags">
            <span v-for="tech in techStack" :key="tech" class="tech-tag">
              {{ tech }}
            </span>
          </div>
        </div>

        <div class="hero-visual">
          <div class="code-window">
            <div class="window-header">
              <div class="window-dots">
                <span></span><span></span><span></span>
              </div>
              <div class="window-title">project.tsx</div>
            </div>
            <div class="window-content">
              <div class="code-line"><span class="code-keyword">const</span> <span class="code-var">project</span> = {</div>
              <div class="code-line">  <span class="code-prop">quality</span>: <span class="code-string">'excellent'</span>,</div>
              <div class="code-line">  <span class="code-prop">speed</span>: <span class="code-string">'fast'</span>,</div>
              <div class="code-line">  <span class="code-prop">team</span>: <span class="code-string">'professional'</span></div>
              <div class="code-line">}</div>
            </div>
          </div>

          <div class="floating-elements">
            <div class="float-card card-1">
              <div class="card-icon">💻</div>
              <div class="card-label">Web开发</div>
            </div>
            <div class="float-card card-2">
              <div class="card-icon">📱</div>
              <div class="card-label">移动应用</div>
            </div>
            <div class="float-card card-3">
              <div class="card-icon">🚀</div>
              <div class="card-label">快速交付</div>
            </div>
            <div class="float-card card-4">
              <div class="card-icon">⚡</div>
              <div class="card-label">高性能</div>
            </div>
            <div class="float-card card-5">
              <div class="card-icon">🎨</div>
              <div class="card-label">精美设计</div>
            </div>
            <div class="float-card card-6">
              <div class="card-icon">🔒</div>
              <div class="card-label">安全可靠</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 数据统计 -->
    <section class="stats-section">
      <div class="container">
        <div class="stats-grid">
          <div v-for="(stat, index) in stats" :key="index" class="stat-item">
            <div class="stat-number">
              <span class="number-value">{{ animatedStats[index] }}</span>
              <span class="number-suffix">{{ stat.suffix }}</span>
            </div>
            <div class="stat-label">{{ stat.label }}</div>
            <div class="stat-bar">
              <div class="stat-bar-fill"></div>
            </div>
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
  position: relative;
  overflow: hidden;
}

/* 背景动画 */
.bg-animation {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  pointer-events: none;
  opacity: 0.3;
}

.grid-lines {
  position: absolute;
  width: 100%;
  height: 100%;
  background-image:
    linear-gradient(var(--border-color) 1px, transparent 1px),
    linear-gradient(90deg, var(--border-color) 1px, transparent 1px);
  background-size: 50px 50px;
  animation: gridMove 20s linear infinite;
}

@keyframes gridMove {
  0% {
    transform: translate(0, 0);
  }
  100% {
    transform: translate(50px, 50px);
  }
}

.floating-particles {
  position: absolute;
  width: 100%;
  height: 100%;
}

.particle {
  position: absolute;
  width: 4px;
  height: 4px;
  background: var(--accent-primary);
  border-radius: 50%;
  animation: particleFloat 10s infinite;
  opacity: 0.6;
}

@keyframes particleFloat {
  0%, 100% {
    transform: translateY(0) translateX(0);
    opacity: 0;
  }
  10% {
    opacity: 0.6;
  }
  90% {
    opacity: 0.6;
  }
  100% {
    transform: translateY(-100vh) translateX(50px);
    opacity: 0;
  }
}

/* 英雄区域 */
.hero {
  min-height: calc(100vh - 70px);
  display: flex;
  align-items: center;
  position: relative;
  background: radial-gradient(ellipse at top, rgba(59, 130, 246, 0.1) 0%, transparent 50%);
}

.hero .container {
  display: grid;
  grid-template-columns: 1.2fr 1fr;
  gap: 4rem;
  align-items: center;
  position: relative;
  z-index: 1;
}

.hero-content {
  animation: fadeInUp 1s ease-out;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  background: linear-gradient(135deg, rgba(59, 130, 246, 0.1), rgba(139, 92, 246, 0.1));
  border: 1px solid var(--accent-primary);
  border-radius: 50px;
  margin-bottom: 2rem;
  animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% {
    box-shadow: 0 0 0 0 rgba(59, 130, 246, 0.4);
  }
  50% {
    box-shadow: 0 0 0 10px rgba(59, 130, 246, 0);
  }
}

.badge-icon {
  font-size: 1.2rem;
}

.badge-text {
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--accent-primary);
}

.hero-title {
  font-size: 4rem;
  font-weight: 900;
  line-height: 1.1;
  margin-bottom: 1.5rem;
}

.title-line {
  display: block;
  color: var(--text-primary);
}

.title-highlight {
  display: block;
  background: var(--accent-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  position: relative;
}

.title-highlight::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 0;
  width: 200px;
  height: 4px;
  background: var(--accent-gradient);
  border-radius: 2px;
}

.hero-description {
  font-size: 1.2rem;
  color: var(--text-secondary);
  margin-bottom: 2.5rem;
  line-height: 1.8;
}

.hero-actions {
  display: flex;
  gap: 1rem;
  margin-bottom: 3rem;
}

.btn-glow {
  position: relative;
  overflow: hidden;
}

.btn-glow::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
  transition: left 0.5s;
}

.btn-glow:hover::before {
  left: 100%;
}

.btn-arrow {
  display: inline-block;
  margin-left: 0.5rem;
  transition: transform 0.3s;
}

.btn-glow:hover .btn-arrow {
  transform: translateX(5px);
}

/* 技术标签云 */
.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
  margin-top: 2rem;
}

.tech-tag {
  padding: 0.5rem 1rem;
  background: var(--bg-secondary);
  border: 1px solid var(--border-color);
  border-radius: 6px;
  font-size: 0.85rem;
  font-weight: 500;
  color: var(--text-secondary);
  transition: all 0.3s;
  cursor: default;
}

.tech-tag:hover {
  background: var(--accent-primary);
  color: white;
  border-color: var(--accent-primary);
  transform: translateY(-2px);
}

/* 代码窗口 */
.hero-visual {
  position: relative;
  height: 500px;
}

.code-window {
  background: var(--bg-card);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: var(--shadow-xl);
  border: 1px solid var(--border-color);
  animation: floatSlow 6s ease-in-out infinite;
}

@keyframes floatSlow {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-15px);
  }
}

.window-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem;
  background: var(--bg-secondary);
  border-bottom: 1px solid var(--border-color);
}

.window-dots {
  display: flex;
  gap: 0.5rem;
}

.window-dots span {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: var(--text-tertiary);
}

.window-dots span:nth-child(1) {
  background: #ff5f56;
}

.window-dots span:nth-child(2) {
  background: #ffbd2e;
}

.window-dots span:nth-child(3) {
  background: #27c93f;
}

.window-title {
  font-size: 0.9rem;
  color: var(--text-secondary);
  font-weight: 500;
}

.window-content {
  padding: 1.5rem;
  font-family: 'Monaco', 'Menlo', monospace;
  font-size: 0.95rem;
  line-height: 1.8;
}

.code-line {
  color: var(--text-primary);
}

.code-keyword {
  color: #c678dd;
}

.code-var {
  color: #e06c75;
}

.code-prop {
  color: #61afef;
}

.code-string {
  color: #98c379;
}

/* 浮动元素 */
.floating-elements {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
}

.float-card {
  position: absolute;
  background: var(--bg-card);
  border-radius: 12px;
  padding: 1rem 1.5rem;
  box-shadow: var(--shadow-lg);
  border: 1px solid var(--border-color);
  display: flex;
  align-items: center;
  gap: 0.75rem;
  animation: float 3s ease-in-out infinite;
  backdrop-filter: blur(10px);
}

.float-card.card-1 {
  top: 10%;
  right: -10%;
  animation-delay: 0s;
}

.float-card.card-2 {
  top: 35%;
  right: -20%;
  animation-delay: 0.5s;
}

.float-card.card-3 {
  top: 60%;
  right: -15%;
  animation-delay: 1s;
}

.float-card.card-4 {
  top: 20%;
  right: 10%;
  animation-delay: 1.5s;
}

.float-card.card-5 {
  top: 75%;
  right: 5%;
  animation-delay: 2s;
}

.float-card.card-6 {
  top: 45%;
  right: 5%;
  animation-delay: 2.5s;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0) rotate(0deg);
  }
  50% {
    transform: translateY(-20px) rotate(2deg);
  }
}

.card-icon {
  font-size: 1.5rem;
}

.card-label {
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--text-primary);
  white-space: nowrap;
}

/* 数据统计 */
.stats-section {
  padding: 4rem 0;
  background: var(--bg-secondary);
  border-top: 1px solid var(--border-color);
  border-bottom: 1px solid var(--border-color);
  position: relative;
  z-index: 1;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 3rem;
}

.stat-item {
  text-align: center;
  position: relative;
}

.stat-number {
  font-size: 3.5rem;
  font-weight: 900;
  background: var(--accent-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 0.5rem;
  display: flex;
  align-items: baseline;
  justify-content: center;
  gap: 0.25rem;
}

.number-value {
  font-size: 3.5rem;
}

.number-suffix {
  font-size: 2rem;
}

.stat-label {
  font-size: 1rem;
  color: var(--text-secondary);
  margin-bottom: 1rem;
}

.stat-bar {
  width: 100%;
  height: 4px;
  background: var(--border-color);
  border-radius: 2px;
  overflow: hidden;
  margin-top: 1rem;
}

.stat-bar-fill {
  height: 100%;
  background: var(--accent-gradient);
  animation: fillBar 2s ease-out forwards;
}

@keyframes fillBar {
  from {
    width: 0;
  }
  to {
    width: 100%;
  }
}

/* 服务介绍 */
.services-section {
  background: var(--bg-primary);
  position: relative;
  z-index: 1;
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
    padding-top: 2rem;
  }

  .hero-badge {
    margin-top: 1rem;
  }

  .hero-visual {
    display: block;
    height: 400px;
    margin-top: 3rem;
  }

  .code-window {
    display: none;
  }

  .floating-elements {
    position: relative;
    height: 400px;
  }

  .float-card {
    position: absolute;
    font-size: 0.85rem;
    padding: 0.75rem 1rem;
  }

  .float-card.card-1 {
    top: 5%;
    left: 5%;
    right: auto;
  }

  .float-card.card-2 {
    top: 5%;
    right: 5%;
  }

  .float-card.card-3 {
    top: 35%;
    left: 10%;
    right: auto;
  }

  .float-card.card-4 {
    top: 35%;
    right: 10%;
  }

  .float-card.card-5 {
    top: 65%;
    left: 5%;
    right: auto;
  }

  .float-card.card-6 {
    top: 65%;
    right: 5%;
  }

  .card-icon {
    font-size: 1.25rem;
  }

  .card-label {
    font-size: 0.8rem;
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
  .hero-badge {
    font-size: 0.85rem;
    padding: 0.4rem 0.8rem;
  }

  .hero-title {
    font-size: 2rem;
  }

  .title-highlight::after {
    width: 150px;
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

  .tech-tags {
    gap: 0.5rem;
  }

  .tech-tag {
    font-size: 0.75rem;
    padding: 0.4rem 0.8rem;
  }

  .hero-visual {
    height: 350px;
  }

  .floating-elements {
    height: 350px;
  }

  .float-card {
    padding: 0.6rem 0.9rem;
  }

  .float-card.card-1 {
    top: 5%;
    left: 2%;
  }

  .float-card.card-2 {
    top: 5%;
    right: 2%;
  }

  .float-card.card-3 {
    top: 35%;
    left: 5%;
  }

  .float-card.card-4 {
    top: 35%;
    right: 5%;
  }

  .float-card.card-5 {
    top: 65%;
    left: 2%;
  }

  .float-card.card-6 {
    top: 65%;
    right: 2%;
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
