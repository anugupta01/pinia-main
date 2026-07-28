<template>
  <div class="welcome">
    <button class="back-btn" @click="goToWelcome" aria-label="Back to Welcome">
      <svg viewBox="0 0 24 24" width="22" height="22" fill="none" stroke="currentColor" stroke-width="2"
        stroke-linecap="round" stroke-linejoin="round">
        <line x1="19" y1="12" x2="5" y2="12" />
        <polyline points="12 19 5 12 12 5" />
      </svg>
    </button>

    <main class="hero">
      <span class="badge">📮 Posts Hub</span>
      <h1 class="title">Welcome to <span>Posts</span></h1>
      <p class="subtitle">
        Discover, read, and share stories from around the world.
        Your feed of ideas starts right here.
      </p>

      <div class="actions">
        <button class="btn btn-primary" @click="router.push('/')">
          Home
        </button>
        <button class="btn btn-ghost" @click="router.push('/about')">
          About Us
        </button>
        <button class="btn btn-ghost" @click="router.push('/posts')">
          Posts
        </button>
      </div>
    </main>

    <!-- decorative floating post cards -->
    <div class="deco" aria-hidden="true">
      <div class="card c1"></div>
      <div class="card c2"></div>
      <div class="card c3"></div>
    </div>
  </div>
</template>

<script setup>
import { useRouter } from "vue-router";

const router = useRouter();
const goToWelcome = () => router.push("/");
</script>

<style scoped>
.welcome {
  position: relative;
  min-height: 100vh;
  display: grid;
  place-items: center;
  overflow: hidden;
  background: radial-gradient(circle at 20% 20%, #1e3a8a 0%, #0f172a 55%, #020617 100%);
  color: #f8fafc;
  font-family: system-ui, -apple-system, "Segoe UI", sans-serif;
}

/* Back button, top-left */
.back-btn {
  position: absolute;
  top: 1.5rem;
  left: 1.5rem;
  z-index: 10;
  display: grid;
  place-items: center;
  width: 44px;
  height: 44px;
  border: 1px solid rgba(248, 250, 252, 0.25);
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.06);
  color: #f8fafc;
  cursor: pointer;
  backdrop-filter: blur(8px);
  transition: transform 0.2s ease, background 0.2s ease;
}

.back-btn:hover {
  background: rgba(255, 255, 255, 0.16);
  transform: translateX(-3px);
}

.hero {
  position: relative;
  z-index: 5;
  text-align: center;
  max-width: 620px;
  padding: 2rem;
}

.badge {
  display: inline-block;
  padding: 0.4rem 1rem;
  margin-bottom: 1.5rem;
  border-radius: 999px;
  background: rgba(96, 165, 250, 0.15);
  border: 1px solid rgba(96, 165, 250, 0.35);
  font-size: 0.85rem;
  letter-spacing: 0.02em;
}

.title {
  font-size: clamp(2.5rem, 6vw, 4rem);
  font-weight: 800;
  line-height: 1.05;
  margin: 0 0 1rem;
}

.title span {
  background: linear-gradient(120deg, #60a5fa, #a78bfa, #f472b6);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.subtitle {
  font-size: 1.1rem;
  line-height: 1.6;
  color: #cbd5e1;
  margin: 0 auto 2.5rem;
  max-width: 460px;
}

.actions {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.btn {
  padding: 0.85rem 2rem;
  border-radius: 12px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  border: 1px solid transparent;
  transition: transform 0.15s ease, box-shadow 0.2s ease, background 0.2s ease;
}

.btn:hover {
  transform: translateY(-2px);
}

.btn-primary {
  background: linear-gradient(120deg, #3b82f6, #6366f1);
  color: #fff;
  box-shadow: 0 8px 24px rgba(59, 130, 246, 0.4);
}

.btn-primary:hover {
  box-shadow: 0 12px 30px rgba(59, 130, 246, 0.55);
}

.btn-ghost {
  background: transparent;
  border-color: rgba(248, 250, 252, 0.3);
  color: #f8fafc;
}

.btn-ghost:hover {
  background: rgba(248, 250, 252, 0.08);
}

.deco {
  position: absolute;
  inset: 0;
  z-index: 1;
}

.card {
  position: absolute;
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(4px);
  animation: float 6s ease-in-out infinite;
}

.c1 {
  width: 130px;
  height: 90px;
  top: 18%;
  left: 12%;
  animation-delay: 0s;
}

.c2 {
  width: 90px;
  height: 120px;
  bottom: 15%;
  right: 14%;
  animation-delay: 1.5s;
}

.c3 {
  width: 70px;
  height: 70px;
  top: 25%;
  right: 22%;
  animation-delay: 3s;
}

@keyframes float {

  0%,
  100% {
    transform: translateY(0) rotate(-3deg);
  }

  50% {
    transform: translateY(-18px) rotate(3deg);
  }
}
</style>