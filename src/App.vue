<script setup>
import { computed, ref } from "vue";
import MechanismSection from "./components/MechanismSection.vue";
import CaseShowcase from "./components/CaseShowcase.vue";

const skillName = "designfigma-builingbuiling";
const copyStatus = ref("复制后可直接粘贴到 Codex 或 Claude Code 终端。");

function siteBaseUrl() {
  if (window.location.protocol !== "http:" && window.location.protocol !== "https:") {
    return "https://your-skill-site.example";
  }

  const viteBase = import.meta.env.BASE_URL || "/";
  const basePath = viteBase !== "/" ? viteBase : currentPageDirectory();
  return new URL(basePath, window.location.origin).href.replace(/\/$/, "");
}

function currentPageDirectory() {
  const pathname = window.location.pathname
    .replace(/\/index\.html$/, "/")
    .replace(/\/$/, "/");

  if (pathname.endsWith("/")) {
    return pathname;
  }

  return pathname.replace(/\/[^/]*$/, "/") || "/";
}

const installCommand = computed(() => {
  return `npx skills add ${siteBaseUrl()} -g -y --agent codex --agent claude-code --skill ${skillName}`;
});

async function copyInstallCommand() {
  try {
    await navigator.clipboard.writeText(installCommand.value);
    copyStatus.value = "已复制安装命令。";
  } catch {
    copyStatus.value = "复制失败，可以手动选中命令。";
  }
}
</script>

<template>
  <main>
    <section class="hero shell" id="top">
      <div class="hero-copy">
        <h1>
          <span>高保真还原</span>
          <span>Figma 设计稿。</span>
        </h1>
        <p class="hero-lede">
          复制一条 npx 安装命令，粘贴到 Codex、Claude Code 或其他支持 Agent Skills 的 AI 编程工具里。这个 skill 会把 Figma 精确节点、蝉圈圈组件规范、真实资产和浏览器视觉验收串成一条清晰流程。
        </p>
      </div>

      <aside class="hero-console" aria-label="Skill 安装状态">
        <div class="console-top">
          <span></span>
          <span></span>
          <span></span>
        </div>
        <div class="console-body">
          <p>npx skills add</p>
          <code>{{ installCommand }}</code>
        </div>
        <div class="support-tags" aria-label="当前支持">
          <span>支持</span>
          <strong>蝉圈圈</strong>
        </div>
        <div class="console-actions">
          <p>{{ copyStatus }}</p>
          <button class="btn btn-primary" type="button" @click="copyInstallCommand">
            复制安装命令
          </button>
        </div>
      </aside>
    </section>

    <MechanismSection />
    <CaseShowcase />
  </main>
</template>
