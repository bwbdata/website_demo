<script setup lang="ts">
import { ref, reactive } from 'vue'

interface FormData {
  name: string
  email: string
  phone: string
  company: string
  service: string
  message: string
}

const formData = reactive<FormData>({
  name: '',
  email: '',
  phone: '',
  company: '',
  service: '网站开发',
  message: ''
})

const isSubmitting = ref(false)
const submitSuccess = ref(false)

const services = [
  '网站开发',
  'APP开发',
  '小程序开发',
  '功能定制',
  '其他'
]

const contactInfo = [
  {
    icon: '📧',
    title: '邮箱',
    content: 'adolphbaofan@163.com',
    link: 'mailto:adolphbaofan@163.com'
  },
  // {
  //   icon: '📱',
  //   title: '电话',
  //   content: '+86 138-0000-0000',
  //   link: 'tel:+8613800000000'
  // },
  {
    icon: '💬',
    title: '微信',
    content: 'elecardone',
    link: ''
  },
  {
    icon: '📍',
    title: '地址',
    content: '浙江省杭州市-黄龙万科中心WeWork氪空间',
    link: ''
  }
]

const socialLinks = [
  { name: 'GitHub', icon: '🐙', url: '#' },
  { name: '微信公众号', icon: '💬', url: '#' },
  { name: '知乎', icon: '📝', url: '#' },
  { name: 'Bilibili', icon: '📺', url: '#' }
]

const handleSubmit = async () => {
  // 简单的表单验证
  if (!formData.name || !formData.email || !formData.phone || !formData.message) {
    alert('请填写所有必填项')
    return
  }

  // 邮箱格式验证
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
  if (!emailRegex.test(formData.email)) {
    alert('请输入有效的邮箱地址')
    return
  }

  // 手机号格式验证
  const phoneRegex = /^1[3-9]\d{9}$/
  if (!phoneRegex.test(formData.phone)) {
    alert('请输入有效的手机号码')
    return
  }

  isSubmitting.value = true

  // 模拟提交
  setTimeout(() => {
    isSubmitting.value = false
    submitSuccess.value = true

    // 重置表单
    Object.assign(formData, {
      name: '',
      email: '',
      phone: '',
      company: '',
      service: '网站开发',
      message: ''
    })

    // 3秒后隐藏成功提示
    setTimeout(() => {
      submitSuccess.value = false
    }, 3000)
  }, 1500)
}
</script>

<template>
  <div class="contact">
    <div class="contact-header">
      <div class="container">
        <h1 class="page-title fade-in">联系我们</h1>
        <p class="page-description fade-in">
          让我们一起将您的想法变为现实
        </p>
      </div>
    </div>

    <section class="section">
      <div class="container">
        <div class="contact-content">
          <!-- 联系表单 -->
          <div class="contact-form-wrapper">
            <h2 class="form-title">在线咨询</h2>
            <p class="form-subtitle">填写表单，我们会尽快与您联系</p>

            <form class="contact-form" @submit.prevent="handleSubmit">
              <div class="form-row">
                <div class="form-group">
                  <label for="name">姓名 *</label>
                  <input
                    id="name"
                    v-model="formData.name"
                    type="text"
                    placeholder="请输入您的姓名"
                    required
                  />
                </div>

                <div class="form-group">
                  <label for="phone">手机号 *</label>
                  <input
                    id="phone"
                    v-model="formData.phone"
                    type="tel"
                    placeholder="请输入手机号"
                    required
                  />
                </div>
              </div>

              <div class="form-row">
                <div class="form-group">
                  <label for="email">邮箱 *</label>
                  <input
                    id="email"
                    v-model="formData.email"
                    type="email"
                    placeholder="请输入邮箱地址"
                    required
                  />
                </div>

                <div class="form-group">
                  <label for="company">公司名称</label>
                  <input
                    id="company"
                    v-model="formData.company"
                    type="text"
                    placeholder="请输入公司名称（选填）"
                  />
                </div>
              </div>

              <div class="form-group">
                <label for="service">服务类型 *</label>
                <select id="service" v-model="formData.service" required>
                  <option v-for="service in services" :key="service" :value="service">
                    {{ service }}
                  </option>
                </select>
              </div>

              <div class="form-group">
                <label for="message">项目描述 *</label>
                <textarea
                  id="message"
                  v-model="formData.message"
                  rows="6"
                  placeholder="请简要描述您的项目需求..."
                  required
                ></textarea>
              </div>

              <button
                type="submit"
                class="btn btn-primary submit-btn"
                :disabled="isSubmitting"
              >
                {{ isSubmitting ? '提交中...' : '提交咨询' }}
              </button>

              <div v-if="submitSuccess" class="success-message">
                ✓ 提交成功！我们会尽快与您联系
              </div>
            </form>
          </div>

          <!-- 联系信息 -->
          <div class="contact-info-wrapper">
            <h2 class="info-title">联系方式</h2>
            <p class="info-subtitle">多种方式与我们取得联系</p>

            <div class="contact-info-list">
              <a
                v-for="(info, index) in contactInfo"
                :key="index"
                :href="info.link || '#'"
                class="contact-info-item card"
                :class="{ 'no-link': !info.link }"
              >
                <div class="info-icon">{{ info.icon }}</div>
                <div class="info-content">
                  <div class="info-label">{{ info.title }}</div>
                  <div class="info-value">{{ info.content }}</div>
                </div>
              </a>
            </div>

            <!-- 工作时间 -->
            <div class="work-hours card">
              <h3 class="work-hours-title">工作时间</h3>
              <div class="work-hours-content">
                <div class="work-hours-item">
                  <span class="day">周一至周五</span>
                  <span class="time">9:00 - 18:00</span>
                </div>
                <div class="work-hours-item">
                  <span class="day">周六</span>
                  <span class="time">10:00 - 17:00</span>
                </div>
                <div class="work-hours-item">
                  <span class="day">周日</span>
                  <span class="time">休息</span>
                </div>
              </div>
            </div>

            <!-- 社交媒体 -->
            <div class="social-links">
              <h3 class="social-title">关注我们</h3>
              <div class="social-grid">
                <a
                  v-for="social in socialLinks"
                  :key="social.name"
                  :href="social.url"
                  class="social-link"
                  :title="social.name"
                >
                  <span class="social-icon">{{ social.icon }}</span>
                  <span class="social-name">{{ social.name }}</span>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- FAQ -->
    <section class="faq-section section">
      <div class="container">
        <h2 class="section-title">常见问题</h2>
        <p class="section-subtitle">
          这里是一些客户经常询问的问题
        </p>

        <div class="faq-list">
          <div class="faq-item card">
            <h3 class="faq-question">项目开发周期一般多久？</h3>
            <p class="faq-answer">
              项目周期取决于具体需求和复杂度。一般来说，简单的网站需要2-4周，复杂的APP或小程序需要2-3个月。我们会在需求沟通后给出详细的时间规划。
            </p>
          </div>

          <div class="faq-item card">
            <h3 class="faq-question">如何收费？</h3>
            <p class="faq-answer">
              我们根据项目的具体需求、功能复杂度和开发周期来报价。会在充分了解需求后提供详细的报价方案，确保价格透明合理。
            </p>
          </div>

          <div class="faq-item card">
            <h3 class="faq-question">提供售后服务吗？</h3>
            <p class="faq-answer">
              是的，我们提供完善的售后服务。项目交付后提供3-6个月的免费维护期，之后可以选择年度维护服务。我们会及时响应和解决问题。
            </p>
          </div>

          <div class="faq-item card">
            <h3 class="faq-question">可以看到开发进度吗？</h3>
            <p class="faq-answer">
              当然可以。我们采用敏捷开发模式，会定期向客户展示开发进度，并及时沟通调整。客户可以随时了解项目状态。
            </p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.contact {
  padding-top: 70px;
}

.contact-header {
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

/* 联系内容 */
.contact-content {
  display: grid;
  grid-template-columns: 1.5fr 1fr;
  gap: 3rem;
}

/* 表单 */
.contact-form-wrapper {
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 16px;
  padding: 2.5rem;
}

.form-title {
  font-size: 1.75rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 0.5rem;
}

.form-subtitle {
  color: var(--text-secondary);
  margin-bottom: 2rem;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-group label {
  font-weight: 600;
  color: var(--text-primary);
  font-size: 0.95rem;
}

.form-group input,
.form-group select,
.form-group textarea {
  padding: 0.875rem;
  border: 2px solid var(--border-color);
  border-radius: 8px;
  background: var(--bg-primary);
  color: var(--text-primary);
  font-size: 1rem;
  transition: all 0.3s ease;
  font-family: inherit;
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--accent-primary);
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
}

.form-group textarea {
  resize: vertical;
  min-height: 120px;
}

.submit-btn {
  width: 100%;
  margin-top: 1rem;
}

.submit-btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.success-message {
  padding: 1rem;
  background: #10b981;
  color: white;
  border-radius: 8px;
  text-align: center;
  font-weight: 600;
  animation: slideInDown 0.3s ease-out;
}

@keyframes slideInDown {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* 联系信息 */
.contact-info-wrapper {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.info-title {
  font-size: 1.75rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 0.5rem;
}

.info-subtitle {
  color: var(--text-secondary);
}

.contact-info-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.contact-info-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1.25rem;
  text-decoration: none;
  transition: all 0.3s ease;
}

.contact-info-item:not(.no-link):hover {
  transform: translateX(5px);
}

.contact-info-item.no-link {
  cursor: default;
}

.info-icon {
  font-size: 2rem;
  flex-shrink: 0;
}

.info-content {
  flex: 1;
}

.info-label {
  font-size: 0.875rem;
  color: var(--text-tertiary);
  margin-bottom: 0.25rem;
}

.info-value {
  font-size: 1rem;
  font-weight: 600;
  color: var(--text-primary);
}

/* 工作时间 */
.work-hours {
  padding: 1.5rem;
}

.work-hours-title {
  font-size: 1.125rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 1rem;
}

.work-hours-content {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.work-hours-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem 0;
  border-bottom: 1px solid var(--border-color);
}

.work-hours-item:last-child {
  border-bottom: none;
}

.day {
  color: var(--text-secondary);
  font-weight: 500;
}

.time {
  color: var(--text-primary);
  font-weight: 600;
}

/* 社交媒体 */
.social-links {
  padding: 1.5rem;
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 12px;
}

.social-title {
  font-size: 1.125rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 1rem;
}

.social-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 0.75rem;
}

.social-link {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  padding: 1rem;
  background: var(--bg-secondary);
  border-radius: 8px;
  text-decoration: none;
  transition: all 0.3s ease;
}

.social-link:hover {
  background: var(--accent-primary);
  transform: translateY(-2px);
}

.social-link:hover .social-icon,
.social-link:hover .social-name {
  color: white;
}

.social-icon {
  font-size: 1.5rem;
}

.social-name {
  font-size: 0.875rem;
  font-weight: 600;
  color: var(--text-primary);
  transition: color 0.3s ease;
}

/* FAQ */
.faq-section {
  background: var(--bg-secondary);
}

.faq-list {
  display: grid;
  gap: 1.5rem;
  max-width: 900px;
  margin: 0 auto;
}

.faq-item {
  padding: 2rem;
}

.faq-question {
  font-size: 1.125rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 1rem;
}

.faq-answer {
  color: var(--text-secondary);
  line-height: 1.7;
}

/* 响应式 */
@media (max-width: 968px) {
  .contact-content {
    grid-template-columns: 1fr;
  }

  .form-row {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 640px) {
  .page-title {
    font-size: 2rem;
  }

  .page-description {
    font-size: 1rem;
  }

  .contact-form-wrapper {
    padding: 1.5rem;
  }

  .social-grid {
    grid-template-columns: 1fr;
  }
}
</style>
