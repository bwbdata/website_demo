<script setup lang="ts">
const contactInfo = [
  {
    icon: '💬',
    title: '微信',
    content: 'elecardone',
    link: '',
    hasQRCode: true
  },
  {
    icon: '📧',
    title: '邮箱',
    content: 'adolphbaofan@163.com',
    link: 'mailto:adolphbaofan@163.com'
  },
  {
    icon: '📍',
    title: '地址',
    content: '浙江省杭州市-黄龙万科中心WeWork',
    link: ''
  }
]
</script>

<template>
  <div class="contact">
    <section class="section">
      <div class="container">
        <div class="contact-content">
          <!-- 联系信息 -->
          <div class="contact-info-wrapper">
            <h2 class="info-title">联系方式</h2>
            <p class="info-subtitle">多种方式与我们取得联系</p>

            <div class="contact-info-list">
              <div
                v-for="(info, index) in contactInfo"
                :key="index"
                class="contact-info-item card"
                :class="{ 'no-link': !info.link, 'has-qrcode': info.hasQRCode }"
              >
                <a
                  v-if="info.link"
                  :href="info.link"
                  class="info-link"
                >
                  <div class="info-icon">{{ info.icon }}</div>
                  <div class="info-content">
                    <div class="info-label">{{ info.title }}</div>
                    <div class="info-value">{{ info.content }}</div>
                  </div>
                </a>
                <div v-else class="info-link">
                  <div class="info-icon">{{ info.icon }}</div>
                  <div class="info-content">
                    <div class="info-label">{{ info.title }}</div>
                    <div class="info-value">{{ info.content }}</div>
                  </div>
                </div>

                <!-- 微信二维码 -->
                <div v-if="info.hasQRCode" class="qrcode-display">
                  <img src="/wechat-qrcode.png" alt="微信二维码" class="qrcode-image" />
                  <p class="qrcode-tip">扫码添加微信</p>
                </div>
              </div>
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
            <!-- <div class="social-links">
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
            </div> -->
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
  display: flex;
  justify-content: center;
  max-width: 800px;
  margin: 0 auto;
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
  position: relative;
  padding: 1.25rem;
  transition: all 0.3s ease;
}

.contact-info-item.has-qrcode {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.info-link {
  display: flex;
  align-items: center;
  gap: 1rem;
  text-decoration: none;
  color: inherit;
  width: 100%;
}

.contact-info-item:not(.no-link) .info-link:hover {
  transform: translateX(5px);
}

.contact-info-item.no-link {
  cursor: default;
}

/* 二维码显示 */
.qrcode-display {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1rem;
  background: var(--bg-secondary);
  border-radius: 8px;
  margin-top: 0.5rem;
}

.qrcode-image {
  width: 180px;
  height: 180px;
  border-radius: 8px;
  margin-bottom: 0.75rem;
  border: 2px solid var(--border-color);
}

.qrcode-tip {
  font-size: 0.875rem;
  color: var(--text-secondary);
  margin: 0;
  font-weight: 600;
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
