<script setup lang="ts">
import { ref } from 'vue'

interface FAQItem {
  question: string
  answer: string
}

const faqs = ref<FAQItem[]>([
  {
    question: '项目开发周期一般多久？',
    answer: '项目周期取决于具体需求和复杂度。一般来说，简单的网站需要2-4周，复杂的APP或小程序需要2-3个月。我们会在需求沟通后给出详细的时间规划。'
  },
  {
    question: '如何收费？',
    answer: '我们根据项目的具体需求、功能复杂度和开发周期来报价。会在充分了解需求后提供详细的报价方案，确保价格透明合理。'
  },
  {
    question: '提供售后服务吗？',
    answer: '是的，我们提供完善的售后服务。项目交付后提供3-6个月的免费维护期，之后可以选择年度维护服务。我们会及时响应和解决问题。'
  },
  {
    question: '可以看到开发进度吗？',
    answer: '当然可以。我们采用敏捷开发模式，会定期向客户展示开发进度，并及时沟通调整。客户可以随时了解项目状态。'
  },
  {
    question: '支持哪些技术栈？',
    answer: '我们精通主流的前端技术（Vue.js、React、TypeScript）、移动端开发（React Native、Flutter、微信小程序）、后端技术（Node.js、Python、Java）以及各类数据库和云服务。'
  },
  {
    question: '可以提供UI/UX设计服务吗？',
    answer: '可以。我们有专业的UI/UX设计师，可以提供从产品原型、交互设计到视觉设计的全流程服务，确保产品既美观又易用。'
  },
  {
    question: '项目交付后提供源代码吗？',
    answer: '是的，项目完成后我们会交付完整的源代码和相关文档，确保客户对项目拥有完全的控制权。'
  },
  {
    question: '如何保证项目质量？',
    answer: '我们有严格的代码审查流程、完善的测试体系，以及经验丰富的技术团队。每个项目都会经过多轮测试和优化，确保交付高质量的产品。'
  }
])
</script>

<template>
  <div class="faq">
    <div class="faq-header">
      <div class="container">
        <h1 class="page-title fade-in">常见问题</h1>
        <p class="page-description fade-in">
          这里是一些客户经常询问的问题
        </p>
      </div>
    </div>

    <section class="section">
      <div class="container">
        <div class="faq-list">
          <div v-for="(faq, index) in faqs" :key="index" class="faq-item card">
            <h3 class="faq-question">{{ faq.question }}</h3>
            <p class="faq-answer">{{ faq.answer }}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.faq {
  padding-top: 70px;
}

.faq-header {
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
@media (max-width: 640px) {
  .page-title {
    font-size: 2rem;
  }

  .page-description {
    font-size: 1rem;
  }

  .faq-item {
    padding: 1.5rem;
  }
}
</style>
