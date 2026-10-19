<script setup lang="ts">
import { ref } from 'vue'

const menuOpen = ref(false)

interface PortfolioProject {
  title: string
  category: string
  year: string
  image: string
  imageAlt: string
  description: string
}

const projects: PortfolioProject[] = []
const currentYear = new Date().getFullYear()

function closeMenu() {
  menuOpen.value = false
}
</script>

<template>
  <div class="site-shell">
    <header class="topbar">
      <a class="wordmark" href="#home" aria-label="Yzd，返回首页" @click="closeMenu">
        <span class="wordmark-mark">YZD</span>
        <span>Yzd<span class="wordmark-dot">.</span></span>
      </a>

      <button
        class="menu-toggle"
        type="button"
        :aria-expanded="menuOpen"
        aria-label="切换导航菜单"
        @click="menuOpen = !menuOpen"
      >
        <span></span>
        <span></span>
      </button>

      <nav class="main-nav" :class="{ 'is-open': menuOpen }" aria-label="主导航">
        <a href="#work" @click="closeMenu">作品集</a>
        <a href="#about" @click="closeMenu">关于我</a>
        <a href="#contact" @click="closeMenu">联系</a>
        <a class="nav-cta" href="#contact" @click="closeMenu">
          <span>作品更新</span>
          <svg viewBox="0 0 18 18" aria-hidden="true">
            <path d="M3.5 9h10m-4-4 4 4-4 4" />
          </svg>
        </a>
      </nav>
    </header>

    <main>
      <section id="home" class="hero">
        <div class="hero-copy">
          <p class="eyebrow"><span class="status-dot"></span> 建模设计师</p>
          <h1>你好，我是 Yzd。<br />让<span class="highlight">想象</span>，<br />有形可见。</h1>
          <p class="hero-intro">
            我是一名建模设计师，正在把想法转化为细致、生动的三维作品。<br class="desktop-break" />
            作品集会随着实际项目逐步更新。
          </p>
          <div class="hero-actions">
            <a class="button button-dark" href="#work">
              看看我的作品
              <svg viewBox="0 0 18 18" aria-hidden="true">
                <path d="M3.5 9h10m-4-4 4 4-4 4" />
              </svg>
            </a>
            <a class="text-link" href="#about">认识一下我 <span>↘</span></a>
          </div>
        </div>

        <div class="hero-art" aria-label="Yzd的建模设计创作插画">
          <div class="art-orbit orbit-one"></div>
          <div class="art-orbit orbit-two"></div>
          <div class="art-sun"></div>
          <div class="art-label label-top">SHAPE YOUR<br />IDEAS</div>
          <div class="art-card art-card-back">
            <span class="card-stamp">空间<br />构想</span>
            <span class="back-lines"></span>
          </div>
          <div class="art-card art-card-front">
            <span class="tiny-label">FORM STUDY</span>
            <span class="card-title">shape<br />your ideas.</span>
            <span class="card-scribble">✳</span>
            <span class="card-caption">让想象变得看得见</span>
          </div>
          <div class="art-flower flower-one">✳</div>
          <div class="art-flower flower-two">✳</div>
          <span class="art-label label-bottom">建模 · 结构 · 细节</span>
          <span class="art-spark spark-one">✦</span>
          <span class="art-spark spark-two">✧</span>
        </div>

        <a class="scroll-note" href="#work"><span></span> 向下探索</a>
        <div class="hero-index">建模设计师 <span>—</span> 四川绵阳 / 中国</div>
      </section>

      <section id="work" class="work-section section-wrap">
        <div class="section-heading">
          <div>
            <p class="eyebrow"><span class="section-number">01</span> MY PORTFOLIO</p>
            <h2>我的<span class="serif-italic">作品集</span><span class="heading-dot">.</span></h2>
          </div>
          <p class="section-aside">当前作品：{{ projects.length }} 件<br />数量随上传的项目自动更新。</p>
        </div>

        <div v-if="projects.length" class="project-grid">
          <a
            v-for="(project, index) in projects"
            :key="project.title"
            class="project-card"
            href="#contact"
          >
            <div class="project-art">
              <img :src="project.image" :alt="project.imageAlt">
              <span class="project-index">{{ String(index + 1).padStart(2, '0') }} / {{ String(projects.length).padStart(2, '0') }}</span>
            </div>
            <div class="project-meta">
              <div>
                <h3>{{ project.title }}</h3>
                <p>{{ project.category }}</p>
              </div>
              <span class="project-year">{{ project.year }}</span>
            </div>
            <p class="project-description">{{ project.description }}</p>
          </a>
        </div>
        <div v-else class="empty-projects">
          <span class="empty-projects-mark">✳</span>
          <p class="empty-projects-title">作品集正在等待第一个项目</p>
          <p>这里暂时留白，上传作品后会在这里展示，项目数量也会自动同步。</p>
        </div>
        <div class="work-footer">
          <span>PORTFOLIO · {{ projects.length }} 件作品</span>
          <span>内容随你的项目持续更新 <span class="footer-spark">✳</span></span>
        </div>
      </section>

      <section id="about" class="about-section">
        <div class="about-inner section-wrap">
          <div class="about-visual">
            <div class="about-photo-art">
              <div class="portrait-sun"></div>
              <div class="portrait-shape portrait-shape-back"></div>
              <div class="portrait-body"></div>
              <div class="portrait-neck"></div>
              <div class="portrait-head"></div>
              <div class="portrait-hair"></div>
              <div class="portrait-eye"></div>
              <div class="portrait-ear"></div>
              <span class="portrait-star">✳</span>
              <span class="portrait-note">KEEP<br />WONDERING</span>
            </div>
            <div class="about-caption"><span>专注观察形体与细节。</span><span>四川绵阳</span></div>
          </div>

          <div class="about-copy">
            <p class="eyebrow"><span class="section-number">02</span> A LITTLE ABOUT ME</p>
            <h2>把想象，<br /><span class="serif-italic">变成看得见的作品。</span></h2>
            <p class="about-paragraph">
              你好，我是 Yzd，一名来自四川绵阳的建模设计师。
              我希望通过建模，把脑海中的想法变成清晰、具体的形体。
            </p>
            <p class="about-paragraph">
              目前设计经验 0 年，正在积累自己的建模作品。
              作品集会根据你上传的实际项目更新，不展示虚构的案例。
            </p>
            <div class="about-facts">
              <div><strong>0</strong><span>年设计经验</span></div>
              <div><strong>{{ projects.length }}</strong><span>件作品</span></div>
              <div class="location-fact"><strong>四川绵阳</strong><span>所在地</span></div>
            </div>
            <a class="text-link about-link" href="#work">查看作品集状态 <span>↘</span></a>
          </div>
        </div>
      </section>

      <section id="contact" class="contact-section section-wrap">
        <div class="contact-topline">
          <p class="eyebrow"><span class="section-number">03</span> WHAT'S NEXT?</p>
          <span class="contact-spark">✳</span>
        </div>
        <h2>等一个好作品，<br /><span class="serif-italic">由你来添上。</span></h2>
        <div class="contact-bottom">
          <p>作品集暂时留白。上传建模作品后，这里会展示项目内容和实际作品数量。<br />期待看到你的创作。</p>
          <a class="button button-dark contact-button" href="#work">
            查看作品集
            <svg viewBox="0 0 18 18" aria-hidden="true">
              <path d="M3.5 9h10m-4-4 4 4-4 4" />
            </svg>
          </a>
        </div>
      </section>
    </main>

    <footer class="site-footer">
      <a class="wordmark footer-wordmark" href="#home">
        <span class="wordmark-mark">YZD</span>
        <span>Yzd<span class="wordmark-dot">.</span></span>
      </a>
      <p>建模设计师 · 四川绵阳<span>© {{ currentYear }} Yzd</span></p>
      <a class="back-top" href="#home">回到顶部 <span>↑</span></a>
    </footer>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Noto+Sans+SC:wght@400;500;600;700;800&family=Noto+Serif+SC:ital,wght@0,500;0,600;1,500;1,600&display=swap');

:root {
  font-family: 'DM Sans', 'Noto Sans SC', sans-serif;
  color: #20231f;
  background: #f8f7f2;
  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-optical-sizing: auto;
  font-weight: 400;
  scroll-behavior: smooth;
  --ink: #20231f;
  --muted: #777971;
  --paper: #f8f7f2;
  --orange: #ee6843;
  --line: #e5e3dc;
}

* {
  box-sizing: border-box;
}

body {
  min-width: 360px;
  margin: 0;
}

button,
a {
  color: inherit;
  font: inherit;
}

a {
  text-decoration: none;
}

button {
  border: 0;
}

.site-shell {
  width: min(100%, 1600px);
  margin: 0 auto;
  overflow: hidden;
  background: var(--paper);
}

.topbar {
  height: 88px;
  padding: 0 8.1%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid rgba(32, 35, 31, 0.08);
  position: relative;
  z-index: 5;
}

.wordmark {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  font-size: 18px;
  font-weight: 700;
  letter-spacing: -0.04em;
}

.wordmark-mark {
  display: grid;
  width: 32px;
  height: 32px;
  place-items: center;
  border-radius: 50%;
  background: var(--ink);
  color: #f8f7f2;
  font-size: 11px;
  letter-spacing: -0.04em;
}

.wordmark-dot {
  color: var(--orange);
}

.main-nav {
  display: flex;
  align-items: center;
  gap: 40px;
  color: #62645e;
  font-size: 13px;
}

.main-nav > a:not(.nav-cta),
.text-link,
.back-top {
  transition: color 180ms ease;
}

.main-nav > a:not(.nav-cta):hover,
.text-link:hover,
.back-top:hover {
  color: var(--orange);
}

.nav-cta {
  min-height: 42px;
  display: inline-flex;
  align-items: center;
  gap: 14px;
  padding: 0 16px;
  border: 1px solid #d8d7d0;
  border-radius: 4px;
  color: var(--ink);
  transition: background 180ms ease, border-color 180ms ease;
}

.nav-cta:hover {
  border-color: var(--ink);
  background: #efeee8;
}

.nav-cta svg,
.button svg {
  width: 17px;
  fill: none;
  stroke: currentColor;
  stroke-width: 1.5;
  transition: transform 180ms ease;
}

.nav-cta:hover svg,
.button:hover svg {
  transform: translateX(3px);
}

.menu-toggle {
  display: none;
}

.hero {
  min-height: 690px;
  padding: 112px 8.1% 84px;
  position: relative;
  display: grid;
  grid-template-columns: 1.05fr 0.95fr;
  align-items: center;
}

.hero-copy {
  position: relative;
  z-index: 1;
  padding-bottom: 14px;
}

.eyebrow {
  margin: 0;
  color: #777971;
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 0.14em;
}

.status-dot {
  display: inline-block;
  width: 7px;
  height: 7px;
  margin: 0 7px 1px 0;
  border-radius: 50%;
  background: #79a77d;
  box-shadow: 0 0 0 4px rgba(121, 167, 125, 0.12);
}

.hero h1 {
  margin: 30px 0 22px;
  font-size: clamp(42px, 5vw, 68px);
  font-weight: 600;
  letter-spacing: -0.07em;
  line-height: 1.34;
}

.highlight {
  position: relative;
  white-space: nowrap;
}

.highlight::after {
  content: '';
  position: absolute;
  z-index: -1;
  left: -2px;
  right: -4px;
  bottom: 7px;
  height: 15px;
  background: #f2c9a8;
  transform: rotate(-1.5deg);
}

.hero-intro {
  margin: 0;
  color: var(--muted);
  font-size: 14px;
  line-height: 2.05;
}

.hero-actions {
  margin-top: 34px;
  display: flex;
  align-items: center;
  gap: 28px;
}

.button {
  min-height: 50px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 26px;
  padding: 0 20px;
  border-radius: 4px;
  font-size: 12px;
  font-weight: 500;
  transition: background 180ms ease, transform 180ms ease;
}

.button-dark {
  background: var(--ink);
  color: #fff;
}

.button-dark:hover {
  background: #3d4038;
  transform: translateY(-2px);
}

.text-link {
  color: #555750;
  font-size: 12px;
}

.text-link span {
  margin-left: 4px;
  color: var(--orange);
}

.hero-art {
  height: 440px;
  position: relative;
  display: grid;
  place-items: center;
  isolation: isolate;
}

.art-orbit {
  position: absolute;
  z-index: -1;
  width: 380px;
  height: 380px;
  border: 1px solid #e9e5d9;
  border-radius: 50%;
}

.orbit-two {
  width: 310px;
  height: 310px;
  border-style: dashed;
  border-color: #e7ddca;
}

.art-sun {
  width: 226px;
  height: 226px;
  position: absolute;
  top: 78px;
  left: 50%;
  border-radius: 50%;
  background: #f2c97f;
  transform: translateX(-42%);
}

.art-card {
  position: absolute;
  width: 226px;
  height: 286px;
  border-radius: 3px;
  box-shadow: 0 24px 55px rgba(69, 52, 31, 0.13);
}

.art-card-back {
  top: 83px;
  left: 23%;
  background: #dd7959;
  transform: rotate(-11deg);
}

.card-stamp {
  position: absolute;
  top: 30px;
  left: 25px;
  color: #f8e6c4;
  font-family: 'Noto Serif SC', serif;
  font-size: 18px;
  line-height: 1.35;
}

.back-lines {
  position: absolute;
  right: 21px;
  bottom: 28px;
  width: 64px;
  height: 64px;
  border: 1px solid rgba(255, 241, 212, 0.68);
  border-radius: 50%;
}

.back-lines::before,
.back-lines::after {
  content: '';
  position: absolute;
  inset: 9px;
  border: 1px solid rgba(255, 241, 212, 0.65);
  border-radius: 50%;
}

.back-lines::after {
  inset: 19px;
}

.art-card-front {
  top: 106px;
  left: 38%;
  overflow: hidden;
  background: #f3eee3;
  transform: rotate(7deg);
}

.art-card-front::after {
  content: '';
  position: absolute;
  right: -55px;
  bottom: -76px;
  width: 190px;
  height: 190px;
  border-radius: 50%;
  background: #92a68b;
}

.tiny-label,
.card-title,
.card-scribble,
.card-caption {
  position: absolute;
  z-index: 1;
}

.tiny-label {
  top: 25px;
  left: 24px;
  color: #878474;
  font-size: 8px;
  letter-spacing: 0.16em;
}

.card-title {
  top: 64px;
  left: 24px;
  color: #394538;
  font-family: 'Noto Serif SC', serif;
  font-size: 35px;
  letter-spacing: -0.07em;
  line-height: 1.18;
}

.card-scribble {
  top: 147px;
  left: 121px;
  color: #e87854;
  font-size: 50px;
  transform: rotate(-15deg);
}

.card-caption {
  left: 24px;
  bottom: 25px;
  color: #545c4c;
  font-family: 'Noto Serif SC', serif;
  font-size: 10px;
}

.art-flower {
  position: absolute;
  z-index: 2;
  color: #e36f4d;
}

.flower-one {
  top: 64px;
  right: 19%;
  font-size: 42px;
  transform: rotate(-10deg);
}

.flower-two {
  bottom: 59px;
  left: 18%;
  color: #7c9476;
  font-size: 30px;
}

.art-label {
  position: absolute;
  color: #848277;
  font-size: 8px;
  letter-spacing: 0.13em;
  line-height: 1.6;
}

.label-top {
  top: 34px;
  left: 19%;
}

.label-bottom {
  right: 10%;
  bottom: 55px;
}

.art-spark {
  position: absolute;
  color: #dd8a54;
  font-size: 26px;
}

.spark-one {
  top: 86px;
  left: 17%;
}

.spark-two {
  right: 15%;
  bottom: 110px;
}

.scroll-note,
.hero-index {
  position: absolute;
  bottom: 33px;
  color: #898a81;
  font-size: 9px;
  letter-spacing: 0.08em;
}

.scroll-note {
  left: 8.1%;
  display: flex;
  align-items: center;
  gap: 10px;
}

.scroll-note span {
  width: 1px;
  height: 28px;
  background: #c5c3ba;
}

.hero-index {
  right: 8.1%;
}

.hero-index span {
  margin: 0 6px;
  color: var(--orange);
}

.section-wrap {
  width: 83.8%;
  max-width: 1320px;
  margin: 0 auto;
}

.work-section {
  padding-top: 110px;
  padding-bottom: 105px;
  border-top: 1px solid var(--line);
}

.section-heading {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  margin-bottom: 42px;
}

.section-number {
  margin-right: 10px;
  color: var(--orange);
}

.section-heading h2,
.about-copy h2,
.contact-section h2 {
  margin: 20px 0 0;
  font-size: clamp(32px, 4vw, 48px);
  font-weight: 600;
  letter-spacing: -0.065em;
  line-height: 1.4;
}

.serif-italic {
  color: #777f6c;
  font-family: 'Noto Serif SC', serif;
  font-weight: 500;
  font-style: italic;
  letter-spacing: -0.08em;
}

.heading-dot {
  color: var(--orange);
}

.section-aside {
  margin: 0 2px 8px 0;
  color: #888980;
  font-size: 11px;
  line-height: 1.9;
}

.empty-projects {
  min-height: 235px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 30px 20px;
  border: 1px dashed #d8d6cd;
  background: #f3f2ec;
  text-align: center;
}

.empty-projects-mark {
  color: var(--orange);
  font-size: 27px;
}

.empty-projects-title {
  margin: 15px 0 0;
  font-family: 'Noto Serif SC', serif;
  font-size: 17px;
}

.empty-projects p:last-child {
  margin: 9px 0 0;
  color: #898a82;
  font-size: 11px;
  line-height: 1.8;
}

.project-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 48px 28px;
}

.project-card {
  min-width: 0;
  display: block;
}

.project-art {
  height: clamp(235px, 29vw, 380px);
  position: relative;
  overflow: hidden;
  isolation: isolate;
  background: #e7e5de;
  transition: transform 250ms ease;
}

.project-art img {
  width: 100%;
  height: 100%;
  display: block;
  object-fit: cover;
}

.project-card:hover .project-art {
  transform: translateY(-4px);
}

.project-index {
  position: absolute;
  z-index: 3;
  top: 18px;
  left: 20px;
  padding: 6px 8px;
  background: rgba(248, 247, 242, 0.86);
  color: var(--ink);
  font-size: 8px;
  letter-spacing: 0.13em;
}

.project-arrow {
  width: 34px;
  height: 34px;
  position: absolute;
  z-index: 4;
  right: 16px;
  bottom: 16px;
  display: grid;
  place-items: center;
  border-radius: 50%;
  background: rgba(248, 247, 242, 0.86);
  color: var(--ink);
  font-size: 15px;
  transition: transform 200ms ease, background 200ms ease;
}

.project-card:hover .project-arrow {
  background: #fff;
  transform: rotate(45deg);
}

.is-island {
  background: #e7d9c0;
}

.island-sun {
  width: 105px;
  height: 105px;
  position: absolute;
  top: 16%;
  left: 53%;
  border-radius: 50%;
  background: #e89b65;
  box-shadow: 0 0 0 13px rgba(232, 155, 101, 0.1);
}

.island-hill {
  width: 75%;
  height: 62%;
  position: absolute;
  bottom: 9%;
  left: -7%;
  border-radius: 50% 50% 0 0;
  transform: rotate(-12deg);
}

.hill-back {
  bottom: 14%;
  left: 37%;
  background: #9ca587;
  transform: rotate(12deg);
}

.hill-front {
  background: #667b6a;
}

.island-water {
  width: 100%;
  height: 20%;
  position: absolute;
  bottom: 0;
  background: #9fb8b4;
  clip-path: polygon(0 25%, 36% 0, 100% 22%, 100% 100%, 0 100%);
}

.island-title {
  position: absolute;
  z-index: 2;
  top: 27%;
  left: 12%;
  color: #f8f1df;
  font-family: 'Noto Serif SC', serif;
  font-size: clamp(26px, 4vw, 44px);
  letter-spacing: 0.08em;
  line-height: 1.4;
  text-shadow: 0 2px 15px rgba(53, 69, 58, 0.18);
}

.island-seal {
  position: absolute;
  z-index: 2;
  right: 13%;
  bottom: 24%;
  padding: 6px 4px;
  border: 1px solid rgba(255, 249, 227, 0.72);
  color: #fff7e2;
  font-family: 'Noto Serif SC', serif;
  font-size: 9px;
  line-height: 1.5;
  text-align: center;
}

.is-morrow {
  background: #d7c7a5;
}

.morrow-sun {
  width: 75%;
  height: 210%;
  position: absolute;
  top: -70%;
  left: 15%;
  border-radius: 50%;
  background: #e8d9bb;
}

.morrow-overline,
.morrow-title,
.morrow-subtitle {
  position: absolute;
  z-index: 2;
  left: 10%;
  color: #473c2e;
}

.morrow-overline {
  top: 22%;
  font-size: 8px;
  letter-spacing: 0.23em;
}

.morrow-title {
  top: 30%;
  font-size: clamp(44px, 7vw, 78px);
  font-weight: 500;
  letter-spacing: -0.095em;
}

.morrow-title span {
  position: relative;
  top: -2em;
  margin-left: 5px;
  font-size: 9px;
  letter-spacing: 0;
}

.morrow-subtitle {
  top: 53%;
  font-family: 'Noto Serif SC', serif;
  font-size: 11px;
  font-style: italic;
  letter-spacing: 0.03em;
}

.coffee-cup {
  width: 105px;
  height: 88px;
  position: absolute;
  z-index: 2;
  right: 17%;
  bottom: 19%;
  border: 7px solid #f5f0e4;
  border-radius: 10px 10px 38px 38px;
  background: #b66f4c;
  box-shadow: 11px 13px 0 rgba(97, 67, 44, 0.15);
  transform: rotate(8deg);
}

.coffee-cup::after {
  content: '';
  width: 23px;
  height: 33px;
  position: absolute;
  top: 17px;
  right: -28px;
  border: 6px solid #f5f0e4;
  border-left: 0;
  border-radius: 0 16px 16px 0;
}

.coffee-cup span {
  width: 52px;
  height: 4px;
  position: absolute;
  top: 12px;
  left: 19px;
  border-radius: 50%;
  background: #76503c;
}

.coffee-shadow {
  width: 150px;
  height: 17px;
  position: absolute;
  right: 10%;
  bottom: 16%;
  border-radius: 50%;
  background: rgba(85, 66, 46, 0.14);
  filter: blur(5px);
}

.is-journal {
  background: #e8a786;
}

.journal-page {
  width: 43%;
  height: 78%;
  position: absolute;
  top: 11%;
  left: 17%;
  z-index: 2;
  padding: 9% 8% 5%;
  background: #f5ebd8;
  box-shadow: 12px 16px 35px rgba(109, 58, 39, 0.16);
  transform: rotate(-7deg);
}

.journal-date,
.journal-note {
  display: block;
  color: #777265;
  font-size: 7px;
  letter-spacing: 0.16em;
}

.journal-title {
  display: block;
  margin-top: 20%;
  color: #415348;
  font-family: 'Noto Serif SC', serif;
  font-size: clamp(30px, 5vw, 55px);
  letter-spacing: 0.1em;
  line-height: 1.25;
}

.journal-line {
  width: 34px;
  height: 1px;
  display: block;
  margin: 12% 0 7%;
  background: #d17d5d;
}

.journal-note {
  font-size: 6px;
}

.journal-sticker {
  position: absolute;
  z-index: 2;
  top: 25%;
  right: 16%;
  width: 74px;
  height: 74px;
  display: grid;
  place-items: center;
  border-radius: 50%;
  background: #e6c764;
  color: #52513e;
  font-family: 'Noto Serif SC', serif;
  font-size: 13px;
  line-height: 1.2;
  text-align: center;
  transform: rotate(10deg);
}

.journal-sticker span {
  color: #c16049;
}

.journal-sun {
  width: 105px;
  height: 105px;
  position: absolute;
  right: 10%;
  bottom: 12%;
  border: 1px solid rgba(255, 241, 217, 0.75);
  border-radius: 50%;
}

.is-spark {
  background: #d5d9c4;
}

.spark-shape {
  position: absolute;
  border-radius: 50%;
}

.shape-a {
  width: 38%;
  height: 75%;
  top: 19%;
  left: 8%;
  background: #e3a36e;
  transform: rotate(33deg);
}

.shape-b {
  width: 34%;
  height: 67%;
  top: 22%;
  left: 30%;
  background: #73917b;
  transform: rotate(-33deg);
  mix-blend-mode: multiply;
}

.shape-c {
  width: 27%;
  height: 53%;
  top: 29%;
  left: 52%;
  background: #e7ce79;
  transform: rotate(33deg);
  mix-blend-mode: multiply;
}

.spark-label,
.spark-title,
.spark-small {
  position: absolute;
  z-index: 2;
  right: 8%;
  color: #f9f3df;
}

.spark-label {
  top: 22%;
  font-size: 7px;
  letter-spacing: 0.15em;
  line-height: 1.6;
}

.spark-title {
  top: 42%;
  font-family: 'Noto Serif SC', serif;
  font-size: clamp(27px, 4vw, 42px);
  letter-spacing: 0.06em;
  line-height: 1.25;
}

.spark-title span {
  margin-left: 2px;
  color: #e8a36d;
}

.spark-small {
  bottom: 21%;
  font-size: 6px;
  letter-spacing: 0.1em;
}

.project-meta {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  margin-top: 17px;
}

.project-meta h3 {
  margin: 0;
  font-size: 14px;
  font-weight: 600;
  letter-spacing: -0.03em;
}

.project-meta p,
.project-description {
  margin: 6px 0 0;
  color: #898a82;
  font-size: 10px;
}

.project-year {
  color: #898a82;
  font-size: 10px;
}

.project-description {
  margin-top: 10px;
  color: #65675f;
  font-size: 11px;
}

.work-footer {
  display: flex;
  justify-content: space-between;
  margin-top: 62px;
  padding-top: 18px;
  border-top: 1px solid var(--line);
  color: #909188;
  font-size: 8px;
  letter-spacing: 0.11em;
}

.footer-spark {
  margin-left: 5px;
  color: var(--orange);
  font-size: 12px;
}

.about-section {
  padding: 100px 0;
  background: #efeee8;
}

.about-inner {
  display: grid;
  grid-template-columns: 0.9fr 1fr;
  align-items: center;
  gap: 10%;
}

.about-visual {
  width: 100%;
  max-width: 430px;
}

.about-photo-art {
  height: 440px;
  position: relative;
  overflow: hidden;
  background: #e5c3a3;
}

.portrait-sun {
  width: 68%;
  aspect-ratio: 1;
  position: absolute;
  top: 10%;
  right: 9%;
  border-radius: 50%;
  background: #eddbb5;
}

.portrait-shape {
  position: absolute;
  width: 90%;
  height: 54%;
  right: -14%;
  bottom: -12%;
  border-radius: 50%;
}

.portrait-shape-back {
  background: #82917a;
  transform: rotate(-25deg);
}

.portrait-body {
  width: 57%;
  height: 48%;
  position: absolute;
  z-index: 2;
  left: 21%;
  bottom: -13%;
  border-radius: 48% 48% 0 0;
  background: #657b71;
  transform: rotate(-4deg);
}

.portrait-neck {
  width: 18%;
  height: 21%;
  position: absolute;
  z-index: 3;
  top: 52%;
  left: 43%;
  background: #d59b77;
}

.portrait-head {
  width: 31%;
  height: 39%;
  position: absolute;
  z-index: 4;
  top: 22%;
  left: 35%;
  border-radius: 47% 47% 46% 46%;
  background: #e7b38e;
  transform: rotate(-4deg);
}

.portrait-hair {
  width: 35%;
  height: 32%;
  position: absolute;
  z-index: 5;
  top: 18%;
  left: 32%;
  border-radius: 50% 48% 34% 28%;
  background: #403c35;
  transform: rotate(-6deg);
}

.portrait-hair::after {
  content: '';
  width: 20%;
  height: 50%;
  position: absolute;
  top: 45%;
  right: 0;
  border-radius: 0 0 12px 12px;
  background: #403c35;
  transform: rotate(-6deg);
}

.portrait-eye {
  width: 5px;
  height: 3px;
  position: absolute;
  z-index: 6;
  top: 39%;
  left: 55%;
  border-radius: 50%;
  background: #423d37;
}

.portrait-ear {
  width: 8px;
  height: 13px;
  position: absolute;
  z-index: 3;
  top: 42%;
  left: 63%;
  border-radius: 50%;
  background: #dda582;
}

.portrait-star {
  position: absolute;
  z-index: 6;
  top: 16%;
  right: 13%;
  color: #e87e57;
  font-size: 38px;
}

.portrait-note {
  position: absolute;
  z-index: 6;
  bottom: 13%;
  left: 8%;
  color: #f7ead4;
  font-size: 8px;
  letter-spacing: 0.17em;
  line-height: 1.7;
}

.about-caption {
  display: flex;
  justify-content: space-between;
  padding-top: 12px;
  color: #818279;
  font-size: 9px;
}

.about-copy h2 {
  margin-top: 22px;
}

.about-paragraph {
  max-width: 490px;
  margin: 23px 0 0;
  color: #72746d;
  font-size: 12px;
  line-height: 2;
}

.about-facts {
  display: flex;
  gap: 40px;
  margin-top: 34px;
  padding-top: 24px;
  border-top: 1px solid #d9d8d1;
}

.about-facts div {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.about-facts strong {
  font-size: 27px;
  font-weight: 500;
  letter-spacing: -0.06em;
}

.about-facts strong span {
  color: var(--orange);
}

.about-facts div > span {
  color: #898a82;
  font-size: 9px;
}

.about-facts .location-fact strong {
  font-size: 16px;
  letter-spacing: -0.04em;
  line-height: 1.7;
}

.about-link {
  display: inline-block;
  margin-top: 28px;
}

.contact-section {
  padding-top: 105px;
  padding-bottom: 110px;
}

.contact-topline {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.contact-spark {
  color: var(--orange);
  font-size: 26px;
}

.contact-section h2 {
  margin-top: 31px;
  font-size: clamp(42px, 6.5vw, 76px);
  line-height: 1.3;
}

.contact-section h2 .serif-italic {
  color: #a06d52;
}

.contact-bottom {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-top: 35px;
}

.contact-bottom p {
  margin: 0;
  color: #818279;
  font-size: 11px;
  line-height: 2;
}

.contact-button {
  min-width: 230px;
  justify-content: space-between;
}

.site-footer {
  min-height: 86px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 8.1%;
  border-top: 1px solid var(--line);
}

.footer-wordmark {
  font-size: 15px;
}

.footer-wordmark .wordmark-mark {
  width: 28px;
  height: 28px;
  font-size: 9px;
}

.site-footer p,
.back-top {
  color: #878980;
  font-size: 9px;
}

.site-footer p span {
  margin-left: 14px;
}

.back-top span {
  margin-left: 5px;
  color: var(--orange);
}

@media (min-width: 1400px) {
  .hero {
    min-height: 760px;
  }
}

@media (max-width: 900px) {
  .topbar {
    height: 76px;
    padding: 0 6%;
  }

  .hero {
    min-height: 620px;
    padding: 90px 6% 70px;
    grid-template-columns: 1.1fr 0.9fr;
  }

  .hero h1 {
    font-size: clamp(42px, 6.1vw, 58px);
  }

  .hero-art {
    transform: scale(0.86);
    transform-origin: center;
  }

  .art-card-back {
    left: 17%;
  }

  .art-card-front {
    left: 33%;
  }

  .section-wrap {
    width: 88%;
  }

  .about-inner {
    gap: 7%;
  }

  .about-photo-art {
    height: 380px;
  }
}

@media (max-width: 680px) {
  body {
    min-width: 320px;
  }

  .topbar {
    height: 68px;
    padding: 0 6%;
  }

  .menu-toggle {
    width: 40px;
    height: 40px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 6px;
    background: transparent;
    cursor: pointer;
  }

  .menu-toggle span {
    width: 19px;
    height: 1px;
    background: var(--ink);
  }

  .main-nav {
    position: absolute;
    top: 67px;
    right: 0;
    left: 0;
    display: none;
    flex-direction: column;
    align-items: stretch;
    gap: 0;
    padding: 8px 6% 20px;
    border-bottom: 1px solid var(--line);
    background: var(--paper);
  }

  .main-nav.is-open {
    display: flex;
  }

  .main-nav > a:not(.nav-cta) {
    padding: 14px 0;
    border-bottom: 1px solid var(--line);
  }

  .nav-cta {
    justify-content: space-between;
    margin-top: 14px;
  }

  .hero {
    min-height: auto;
    padding: 77px 7% 82px;
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }

  .hero-copy {
    padding: 0;
  }

  .eyebrow {
    font-size: 9px;
  }

  .hero h1 {
    margin: 25px 0 17px;
    font-size: clamp(41px, 11vw, 58px);
    line-height: 1.35;
  }

  .hero-intro {
    max-width: 360px;
    font-size: 12px;
  }

  .desktop-break {
    display: none;
  }

  .hero-actions {
    gap: 20px;
    margin-top: 25px;
  }

  .button {
    min-height: 46px;
    gap: 16px;
    padding: 0 14px;
    font-size: 11px;
  }

  .hero-art {
    height: 330px;
    margin-top: 23px;
    transform: scale(0.79);
    transform-origin: center;
  }

  .art-orbit {
    width: 330px;
    height: 330px;
  }

  .orbit-two {
    width: 275px;
    height: 275px;
  }

  .art-sun {
    width: 190px;
    height: 190px;
    top: 54px;
  }

  .art-card-back {
    top: 57px;
    left: 20%;
  }

  .art-card-front {
    top: 79px;
    left: 36%;
  }

  .flower-one {
    top: 39px;
    right: 14%;
  }

  .flower-two {
    bottom: 39px;
    left: 13%;
  }

  .label-top {
    top: 22px;
    left: 12%;
  }

  .label-bottom {
    right: 4%;
    bottom: 38px;
  }

  .spark-one {
    left: 10%;
  }

  .spark-two {
    right: 8%;
    bottom: 90px;
  }

  .scroll-note {
    left: 7%;
    bottom: 24px;
  }

  .hero-index {
    right: 7%;
    bottom: 31px;
    font-size: 8px;
  }

  .section-wrap {
    width: 86%;
  }

  .work-section {
    padding-top: 76px;
    padding-bottom: 70px;
  }

  .section-heading {
    display: block;
    margin-bottom: 28px;
  }

  .section-heading h2,
  .about-copy h2 {
    margin-top: 14px;
    font-size: 34px;
  }

  .section-aside {
    margin-top: 13px;
    font-size: 10px;
  }

  .project-grid {
    grid-template-columns: 1fr;
    gap: 30px;
  }

  .project-art {
    height: clamp(250px, 76vw, 380px);
  }

  .island-title {
    font-size: 38px;
  }

  .morrow-title {
    font-size: 66px;
  }

  .journal-title {
    font-size: 46px;
  }

  .spark-title {
    font-size: 38px;
  }

  .work-footer {
    gap: 15px;
    margin-top: 38px;
    font-size: 7px;
    letter-spacing: 0.05em;
  }

  .about-section {
    padding: 70px 0 76px;
  }

  .about-inner {
    grid-template-columns: 1fr;
    gap: 42px;
  }

  .about-visual {
    max-width: 100%;
  }

  .about-photo-art {
    height: min(105vw, 410px);
  }

  .about-copy h2 {
    font-size: 37px;
  }

  .about-paragraph {
    margin-top: 18px;
    font-size: 11px;
  }

  .about-facts {
    justify-content: space-between;
    gap: 14px;
    margin-top: 26px;
    padding-top: 19px;
  }

  .about-facts strong {
    font-size: 24px;
  }

  .about-facts div > span {
    font-size: 8px;
  }

  .contact-section {
    padding-top: 76px;
    padding-bottom: 77px;
  }

  .contact-section h2 {
    margin-top: 23px;
    font-size: 46px;
  }

  .contact-bottom {
    align-items: flex-start;
    flex-direction: column;
    gap: 23px;
    margin-top: 23px;
  }

  .contact-bottom p {
    font-size: 10px;
  }

  .site-footer {
    min-height: 75px;
    padding: 0 6%;
  }

  .site-footer p {
    max-width: 120px;
    font-size: 8px;
    line-height: 1.8;
    text-align: center;
  }

  .site-footer p span {
    margin-left: 0;
  }

  .back-top {
    font-size: 8px;
  }
}

@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    scroll-behavior: auto !important;
    transition-duration: 0.01ms !important;
  }
}
</style>
