<script setup lang="ts">
import { ref } from 'vue'

interface Project {
  id: number
  title: string
  category: string
  description: string
  image: string
  tags: string[]
  link?: string
}

const categories = ref(['全部', '网站开发', 'APP开发', '小程序', '其他'])
const activeCategory = ref('全部')

const projects = ref<Project[]>([
  {
    id: 1,
    title: '黑白蜂健康',
    category: '网站开发',
    description: '专业的健康管理平台，提供健康咨询、体检预约、健康档案管理等功能',
    image: '🏥',
    tags: ['Vue 3', 'TypeScript', '健康管理'],
    link: 'https://bwb-health.netlify.app/'
  },
  {
    id: 2,
    title: '黑白蜂摄影',
    category: '网站开发',
    description: '精美的摄影作品展示平台，支持作品分类、在线预约、摄影服务等功能',
    image: '📷',
    tags: ['Vue 3', 'TypeScript', '作品展示'],
    link: 'https://bwb-photo.netlify.app/'
  },
  {
    id: 3,
    title: '企业官网设计',
    category: '网站开发',
    description: '为某科技公司打造的现代化企业官网，采用响应式设计，支持多端访问',
    image: '🏢',
    tags: ['Vue 3', 'TypeScript', '响应式设计']
  },
  {
    id: 4,
    title: '电商平台开发',
    category: '网站开发',
    description: '完整的电商解决方案，包含商品管理、订单系统、支付集成等功能',
    image: '🛒',
    tags: ['React', 'Node.js', '微信支付']
  },
  {
    id: 5,
    title: '健身APP',
    category: 'APP开发',
    description: 'iOS和Android双平台健身应用，提供训练计划、数据追踪等功能',
    image: '💪',
    tags: ['React Native', 'iOS', 'Android']
  },
  {
    id: 6,
    title: '外卖配送APP',
    category: 'APP开发',
    description: '实时定位、订单管理、骑手调度系统的完整外卖配送解决方案',
    image: '🚴',
    tags: ['Flutter', '地图API', '实时通信']
  },
  {
    id: 7,
    title: '在线教育小程序',
    category: '小程序',
    description: '微信小程序在线教育平台，支持视频课程、直播、作业提交等功能',
    image: '📚',
    tags: ['微信小程序', '视频播放', '直播']
  },
  {
    id: 8,
    title: '餐饮点餐小程序',
    category: '小程序',
    description: '扫码点餐、在线支付、会员管理的智能餐饮小程序',
    image: '🍽️',
    tags: ['微信小程序', '支付', '会员系统']
  },
  {
    id: 9,
    title: '智能家居控制系统',
    category: '其他',
    description: '物联网智能家居控制平台，支持多设备联动和远程控制',
    image: '🏠',
    tags: ['IoT', 'WebSocket', '实时控制']
  },
  {
    id: 10,
    title: '数据可视化大屏',
    category: '其他',
    description: '企业数据可视化展示大屏，实时数据更新和多维度分析',
    image: '📊',
    tags: ['ECharts', 'WebSocket', '数据可视化']
  }
])

const filteredProjects = ref<Project[]>(projects.value)

const filterProjects = (category: string) => {
  activeCategory.value = category
  if (category === '全部') {
    filteredProjects.value = projects.value
  } else {
    filteredProjects.value = projects.value.filter(p => p.category === category)
  }
}
</script>

<template>
  <div class="portfolio">
    <section class="section">
      <div class="container">
        <!-- 分类筛选 -->
        <div class="category-filter">
          <button
            v-for="category in categories"
            :key="category"
            class="category-btn"
            :class="{ active: activeCategory === category }"
            @click="filterProjects(category)"
          >
            {{ category }}
          </button>
        </div>

        <!-- 项目网格 -->
        <div class="projects-grid">
          <a
            v-for="project in filteredProjects"
            :key="project.id"
            :href="project.link"
            :target="project.link ? '_blank' : undefined"
            :rel="project.link ? 'noopener noreferrer' : undefined"
            class="project-card card scale-in"
            :class="{ 'has-link': project.link }"
          >
            <div class="project-image">
              <div class="project-emoji">{{ project.image }}</div>
              <div class="project-overlay">
                <button class="view-btn">{{ project.link ? '访问网站' : '查看详情' }}</button>
              </div>
            </div>
            <div class="project-content">
              <div class="project-category">{{ project.category }}</div>
              <h3 class="project-title">{{ project.title }}</h3>
              <p class="project-description">{{ project.description }}</p>
              <div class="project-tags">
                <span v-for="tag in project.tags" :key="tag" class="tag">
                  {{ tag }}
                </span>
              </div>
            </div>
          </a>
        </div>

        <!-- 空状态 -->
        <div v-if="filteredProjects.length === 0" class="empty-state">
          <div class="empty-icon">📭</div>
          <p class="empty-text">暂无相关案例</p>
        </div>
      </div>
    </section>

    <!-- 合作品牌 -->
    <section class="brands-section section">
      <div class="container">
        <h2 class="section-title">合作伙伴</h2>
        <p class="section-subtitle">感谢以下企业的信任与支持</p>

        <div class="brands-grid">
          <div v-for="i in 8" :key="i" class="brand-item">
            <div class="brand-logo">🏢</div>
            <div class="brand-name">合作企业 {{ i }}</div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.portfolio {
  padding-top: 70px;
}

.portfolio-header {
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

/* 分类筛选 */
.category-filter {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 3rem;
  flex-wrap: wrap;
}

.category-btn {
  padding: 0.75rem 1.5rem;
  border: 2px solid var(--border-color);
  background: var(--bg-card);
  color: var(--text-secondary);
  border-radius: 50px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.category-btn:hover {
  border-color: var(--accent-primary);
  color: var(--accent-primary);
}

.category-btn.active {
  background: var(--accent-gradient);
  border-color: transparent;
  color: white;
}

/* 项目网格 */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 2rem;
}

.project-card {
  overflow: hidden;
  cursor: pointer;
  text-decoration: none;
  color: inherit;
  display: block;
}

.project-card.has-link:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
}

.project-image {
  position: relative;
  height: 200px;
  background: var(--bg-secondary);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.project-emoji {
  font-size: 5rem;
  transition: transform 0.3s ease;
}

.project-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(59, 130, 246, 0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.project-card:hover .project-overlay {
  opacity: 1;
}

.project-card:hover .project-emoji {
  transform: scale(1.1);
}

.view-btn {
  padding: 0.75rem 2rem;
  background: white;
  color: var(--accent-primary);
  border: none;
  border-radius: 8px;
  font-weight: 600;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.view-btn:hover {
  transform: scale(1.05);
}

.project-content {
  padding: 1.5rem;
}

.project-category {
  display: inline-block;
  padding: 0.25rem 0.75rem;
  background: var(--bg-secondary);
  color: var(--accent-primary);
  border-radius: 4px;
  font-size: 0.875rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.project-title {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 0.75rem;
}

.project-description {
  color: var(--text-secondary);
  line-height: 1.6;
  margin-bottom: 1rem;
  font-size: 0.95rem;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tag {
  padding: 0.25rem 0.75rem;
  background: var(--bg-secondary);
  color: var(--text-secondary);
  border-radius: 4px;
  font-size: 0.875rem;
}

/* 空状态 */
.empty-state {
  text-align: center;
  padding: 4rem 0;
}

.empty-icon {
  font-size: 4rem;
  margin-bottom: 1rem;
}

.empty-text {
  font-size: 1.125rem;
  color: var(--text-secondary);
}

/* 合作品牌 */
.brands-section {
  background: var(--bg-secondary);
}

.brands-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 2rem;
}

.brand-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.75rem;
  padding: 2rem;
  background: var(--bg-card);
  border-radius: 12px;
  border: 1px solid var(--border-color);
  transition: all 0.3s ease;
}

.brand-item:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-lg);
}

.brand-logo {
  font-size: 3rem;
  opacity: 0.6;
}

.brand-name {
  font-size: 0.875rem;
  color: var(--text-secondary);
  font-weight: 600;
}

/* 响应式 */
@media (max-width: 768px) {
  .page-title {
    font-size: 2rem;
  }

  .page-description {
    font-size: 1rem;
  }

  .projects-grid {
    grid-template-columns: 1fr;
  }

  .brands-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
