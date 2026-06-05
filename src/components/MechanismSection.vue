<script setup>
const steps = [
  {
    index: "01",
    title: "Figma 节点先行",
    text: "必须拿到 node-id，读取 frame、组件、变量、切图、mask 和 Code Connect 映射，不凭截图猜结构。",
  },
  {
    index: "02",
    title: "按需加载规范",
    text: "只有明确属于蝉圈圈时才加载规范，优先级是 Figma 变量与样式、项目组件、项目 token、组件库 token。",
  },
  {
    index: "03",
    title: "真实资产进入工程",
    text: "Figma 返回的图片、SVG、icon 和 mask 要下载到项目资产目录，不用相似 icon 或大块截图替代。",
  },
  {
    index: "04",
    title: "浏览器视觉验收",
    text: "启动页面截图，对照 Figma 检查颜色、裁切、圆角、阴影、透明度和交互状态，避免假 UI。",
  },
];
</script>

<template>
  <section class="mechanism shell" id="mechanism">
    <div class="section-heading">
      <h2>像设计部交付规范一样约束 AI，而不是让 AI 自由发挥。</h2>
      <p>
        这个 skill 的核心价值是把“高保真还原”拆成可执行、可检查、可追责的步骤，尤其适合蝉圈圈这种业务系统型页面。
      </p>
    </div>

    <div class="mechanism-grid">
      <article v-for="step in steps" :key="step.index" class="mechanism-card">
        <span>{{ step.index }}</span>
        <h3>{{ step.title }}</h3>
        <p>{{ step.text }}</p>
      </article>
    </div>
  </section>
</template>
