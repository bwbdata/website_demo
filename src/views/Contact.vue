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
                  <span class="day">周六、周日</span>
                  <span class="time">打工人不休息</span>
                </div>
              </div>
            </div>
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

/* 联系信息 */
.contact-info-wrapper {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  width: 100%;
}

.contact-info-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.contact-info-item {
  position: relative;
  padding: 1.5rem;
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
  padding: 1.5rem;
  background: var(--bg-secondary);
  border-radius: 12px;
  margin-top: 0.5rem;
}

.qrcode-image {
  width: 200px;
  height: 200px;
  border-radius: 12px;
  margin-bottom: 1rem;
  border: 2px solid var(--border-color);
  box-shadow: var(--shadow-md);
}

.qrcode-tip {
  font-size: 0.95rem;
  color: var(--text-secondary);
  margin: 0;
  font-weight: 600;
}

.info-icon {
  font-size: 2.5rem;
  flex-shrink: 0;
}

.info-content {
  flex: 1;
}

.info-label {
  font-size: 0.95rem;
  color: var(--text-tertiary);
  margin-bottom: 0.5rem;
}

.info-value {
  font-size: 1.125rem;
  font-weight: 600;
  color: var(--text-primary);
}

/* 工作时间 */
.work-hours {
  padding: 2rem;
}

.work-hours-title {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 1.5rem;
  text-align: center;
}

.work-hours-content {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.work-hours-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.75rem 0;
  border-bottom: 1px solid var(--border-color);
}

.work-hours-item:last-child {
  border-bottom: none;
}

.day {
  color: var(--text-secondary);
  font-weight: 500;
  font-size: 1rem;
}

.time {
  color: var(--text-primary);
  font-weight: 600;
  font-size: 1rem;
}

/* 响应式 */
@media (max-width: 640px) {
  .page-title {
    font-size: 2rem;
  }

  .page-description {
    font-size: 1rem;
  }

  .contact-info-item {
    padding: 1.25rem;
  }

  .qrcode-image {
    width: 180px;
    height: 180px;
  }

  .work-hours {
    padding: 1.5rem;
  }
}
</style>
