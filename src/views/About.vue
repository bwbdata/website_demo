<script setup lang="ts">
import { ref } from 'vue'

interface TeamMember {
  name: string
  role: string
  avatar: string
  description: string
}

interface Value {
  icon: string
  title: string
  description: string
}

const teamMembers = ref<TeamMember[]>([
  {
    name: '秀吉',
    role: '产品经理 / 前端开发 / 移动端开发',
    avatar: '👨‍💼',
    description: '前阿里巴巴高级产品专家，多年产品经验，同时精通前端/移动端开发，主导过多个千万级用户产品'
  },
  {
    name: '青山 (Alex)',
    role: '前端高级工程师',
    avatar: '👨‍💻',
    description: '前阿里巴巴高级前端工程师，8年前端开发经验，精通Vue/React生态'
  },
  {
    name: '流云 (Cloud)',
    role: '前端高级工程师',
    avatar: '👨‍💻',
    description: '前字节跳动前端开发，擅长性能优化和工程化，开源贡献者'
  },
  {
    name: 'Kevin',
    role: '后端架构师',
    avatar: '👨‍💼',
    description: '前腾讯后端专家，10年后端开发经验，精通微服务架构和高并发系统'
  },
  {
    name: '诗诗',
    role: 'UI/UX设计师',
    avatar: '👩‍🎨',
    description: '前美团资深设计师，擅长品牌视觉和交互设计'
  },
  
])

const values = ref<Value[]>([
  {
    icon: '🎯',
    title: '专业专注',
    description: '专注于数字产品开发，用专业的技术和服务为客户创造价值'
  },
  {
    icon: '💡',
    title: '创新驱动',
    description: '持续关注新技术，为客户提供创新的解决方案'
  },
  {
    icon: '🤝',
    title: '客户至上',
    description: '以客户需求为导向，提供贴心的服务和支持'
  },
  {
    icon: '⚡',
    title: '高效交付',
    description: '严格的项目管理流程，确保按时高质量交付'
  }
])

const timeline = ref([
  { year: '2025.07', event: '黑白蜂工作室正式成立，汇聚大厂精英，开启创业征程' },
  { year: '2025.08', event: '完成首批客户项目，获得高度认可，建立良好口碑' },
  { year: '2025.09', event: '业务快速增长，服务范围覆盖网站、APP、小程序全领域' },
  { year: '2025.10', event: '推出定制化解决方案，为多家企业提供数字化转型服务' },
  { year: '2025.11', event: '团队持续扩展，技术实力不断提升，项目交付能力增强' },
  { year: '未来', event: '致力于成为行业领先的技术服务商，为更多客户创造价值' }
])
</script>

<template>
  <div class="about">
    <!-- 公司介绍 -->
    <section class="intro-section section">
      <div class="container">
        <div class="intro-content">
          <div class="intro-text">
            <h2 class="section-title" style="text-align: left;">我们是谁</h2>
            <p class="intro-paragraph">
              黑白蜂工作室是一家专注于数字产品开发的技术工作室，成立于2025年7月。我们拥有一支经验丰富、充满激情的技术团队，致力于为客户提供高质量的网站、APP、小程序等数字化解决方案。
            </p>
            <p class="intro-paragraph">
              我们相信技术的力量可以改变世界，通过创新的思维和专业的技术，帮助企业实现数字化转型，提升业务效率，创造更大的商业价值。
            </p>
            <p class="intro-paragraph">
              多年来，我们已经为100+家企业提供了专业的技术服务，涵盖电商、教育、医疗、金融等多个行业领域，赢得了客户的广泛认可和信赖。
            </p>
          </div>
          <div class="intro-visual">
            <div class="visual-card">
              <div class="visual-icon">🚀</div>
              <div class="visual-text">持续创新</div>
            </div>
            <div class="visual-card">
              <div class="visual-icon">💼</div>
              <div class="visual-text">专业团队</div>
            </div>
            <div class="visual-card">
              <div class="visual-icon">⭐</div>
              <div class="visual-text">优质服务</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 核心价值观 -->
    <section class="values-section section">
      <div class="container">
        <h2 class="section-title">核心价值观</h2>
        <p class="section-subtitle">
          我们坚持的理念和追求的目标
        </p>

        <div class="values-grid">
          <div v-for="(value, index) in values" :key="index" class="value-card card">
            <div class="value-icon">{{ value.icon }}</div>
            <h3 class="value-title">{{ value.title }}</h3>
            <p class="value-description">{{ value.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 团队介绍 -->
    <section class="team-section section">
      <div class="container">
        <h2 class="section-title">核心团队</h2>
        <p class="section-subtitle">
          经验丰富、充满激情的专业团队
        </p>

        <div class="team-grid">
          <div v-for="member in teamMembers" :key="member.name" class="team-card card">
            <div class="member-avatar">{{ member.avatar }}</div>
            <h3 class="member-name">{{ member.name }}</h3>
            <div class="member-role">{{ member.role }}</div>
            <p class="member-description">{{ member.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 发展历程 -->
    <section class="timeline-section section">
      <div class="container">
        <h2 class="section-title">发展历程</h2>
        <p class="section-subtitle">
          我们的成长之路
        </p>

        <div class="timeline">
          <div
            v-for="(item, index) in timeline"
            :key="index"
            class="timeline-item"
            :class="{ 'timeline-item-right': index % 2 === 1 }"
          >
            <div class="timeline-year">{{ item.year }}</div>
            <div class="timeline-content card">
              <p>{{ item.event }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 技术栈 -->
    <section class="tech-section section">
      <div class="container">
        <h2 class="section-title">技术栈</h2>
        <p class="section-subtitle">
          我们使用的主流技术和工具
        </p>

        <div class="tech-categories">
          <div class="tech-category">
            <h3 class="tech-category-title">前端技术</h3>
            <div class="tech-tags">
              <span class="tech-tag">Vue.js</span>
              <span class="tech-tag">React</span>
              <span class="tech-tag">TypeScript</span>
              <span class="tech-tag">Tailwind CSS</span>
              <span class="tech-tag">Vite</span>
            </div>
          </div>

          <div class="tech-category">
            <h3 class="tech-category-title">移动端</h3>
            <div class="tech-tags">
              <span class="tech-tag">React Native</span>
              <span class="tech-tag">Flutter</span>
              <span class="tech-tag">微信小程序</span>
              <span class="tech-tag">uni-app</span>
            </div>
          </div>

          <div class="tech-category">
            <h3 class="tech-category-title">后端技术</h3>
            <div class="tech-tags">
              <span class="tech-tag">Node.js</span>
              <span class="tech-tag">Python</span>
              <span class="tech-tag">Java</span>
              <span class="tech-tag">MySQL</span>
              <span class="tech-tag">MongoDB</span>
              <span class="tech-tag">Redis</span>
            </div>
          </div>

          <div class="tech-category">
            <h3 class="tech-category-title">DevOps</h3>
            <div class="tech-tags">
              <span class="tech-tag">Docker</span>
              <span class="tech-tag">Git</span>
              <span class="tech-tag">CI/CD</span>
              <span class="tech-tag">云服务</span>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.about {
  padding-top: 70px;
}

.about-header {
  padding: 6rem 0 4rem;
  background: linear-gradient(135deg, var(--bg-primary) 0%, var(--bg-secondary) 100%);
  text-align: center;
  border-bottom: 1px solid var(--border-color);
}

.page-title {
  font-size: 3rem;
  font-weight: 800;
  margin-bottom: 1rem;
  background: var(--accent-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.page-description {
  font-size: 1.25rem;
  color: var(--text-secondary);
}

/* 公司介绍 */
.intro-section {
  background: var(--bg-primary);
}

.intro-content {
  display: grid;
  grid-template-columns: 1.5fr 1fr;
  gap: 4rem;
  align-items: center;
}

.intro-text {
  max-width: 700px;
}

.intro-paragraph {
  color: var(--text-secondary);
  line-height: 1.8;
  margin-bottom: 1.5rem;
  font-size: 1.05rem;
}

.intro-visual {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.visual-card {
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  padding: 1.5rem;
  display: flex;
  align-items: center;
  gap: 1rem;
  transition: all 0.3s ease;
}

.visual-card:hover {
  transform: translateX(10px);
  box-shadow: var(--shadow-lg);
}

.visual-icon {
  font-size: 2.5rem;
}

.visual-text {
  font-size: 1.125rem;
  font-weight: 600;
  color: var(--text-primary);
}

/* 核心价值观 */
.values-section {
  background: var(--bg-secondary);
}

.values-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.value-card {
  text-align: center;
}

.value-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.value-title {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 0.75rem;
}

.value-description {
  color: var(--text-secondary);
  line-height: 1.6;
}

/* 团队介绍 */
.team-section {
  background: var(--bg-primary);
}

.team-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.team-card {
  text-align: center;
}

.member-avatar {
  font-size: 4rem;
  margin-bottom: 1rem;
}

.member-name {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 0.5rem;
}

.member-role {
  color: var(--accent-primary);
  font-weight: 600;
  margin-bottom: 1rem;
}

.member-description {
  color: var(--text-secondary);
  line-height: 1.6;
  font-size: 0.95rem;
}

/* 发展历程 */
.timeline-section {
  background: var(--bg-secondary);
}

.timeline {
  max-width: 800px;
  margin: 0 auto;
  position: relative;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 50%;
  top: 0;
  bottom: 0;
  width: 2px;
  background: var(--border-color);
  transform: translateX(-50%);
}

.timeline-item {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  gap: 2rem;
  margin-bottom: 3rem;
  align-items: center;
}

.timeline-year {
  text-align: right;
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--accent-primary);
}

.timeline-item-right .timeline-year {
  order: 3;
  text-align: left;
}

.timeline-content {
  grid-column: 3;
  position: relative;
}

.timeline-item-right .timeline-content {
  grid-column: 1;
}

.timeline-content::before {
  content: '';
  position: absolute;
  left: -2rem;
  top: 50%;
  width: 12px;
  height: 12px;
  background: var(--accent-primary);
  border-radius: 50%;
  transform: translateY(-50%);
}

.timeline-item-right .timeline-content::before {
  left: auto;
  right: -2rem;
}

.timeline-content p {
  color: var(--text-secondary);
  line-height: 1.6;
}

/* 技术栈 */
.tech-section {
  background: var(--bg-primary);
}

.tech-categories {
  display: grid;
  gap: 3rem;
}

.tech-category {
  text-align: center;
}

.tech-category-title {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 1.5rem;
}

.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
}

.tech-tag {
  padding: 0.75rem 1.5rem;
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 8px;
  color: var(--text-primary);
  font-weight: 600;
  transition: all 0.3s ease;
}

.tech-tag:hover {
  background: var(--accent-gradient);
  color: white;
  border-color: transparent;
  transform: translateY(-2px);
}

/* 响应式 */
@media (max-width: 968px) {
  .intro-content {
    grid-template-columns: 1fr;
  }

  .timeline::before {
    left: 0;
  }

  .timeline-item {
    grid-template-columns: auto 1fr;
    gap: 1rem;
  }

  .timeline-year {
    text-align: left;
    font-size: 1.25rem;
  }

  .timeline-item-right .timeline-year {
    order: 1;
  }

  .timeline-content {
    grid-column: 2;
  }

  .timeline-item-right .timeline-content {
    grid-column: 2;
  }

  .timeline-content::before {
    left: -1.5rem;
  }

  .timeline-item-right .timeline-content::before {
    left: -1.5rem;
    right: auto;
  }
}

@media (max-width: 640px) {
  .page-title {
    font-size: 2rem;
  }

  .page-description {
    font-size: 1rem;
  }
}
</style>
