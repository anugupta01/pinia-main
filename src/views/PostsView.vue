<template>
  <div class="posts">
    <button class="back-btn" @click="router.push('/')" aria-label="Back to Welcome">
      <svg viewBox="0 0 24 24" width="22" height="22" fill="none" stroke="currentColor" stroke-width="2"
        stroke-linecap="round" stroke-linejoin="round">
        <line x1="19" y1="12" x2="5" y2="12" />
        <polyline points="12 19 5 12 12 5" />
      </svg>
    </button>

    <main class="content">
      <span class="badge">📮 Posts Hub</span>
      <h1 class="title">All <span>Posts</span></h1>

      <div class="post-grid">
        <router-link v-for="post in store.posts" :key="post.id" :to="`/posts/${post.id}`" class="post-card">
          <h3 class="post-title">{{ post.title }}</h3>
          <span class="read-more">Read more →</span>
        </router-link>
      </div>
    </main>

    <div class="deco" aria-hidden="true">
      <div class="card c1"></div>
      <div class="card c2"></div>
      <div class="card c3"></div>
    </div>
  </div>
</template>

<script setup>
import { onMounted } from "vue";
import { useRouter } from "vue-router";
import { usePostStore } from "@/stores/post";

const router = useRouter();
const store = usePostStore();

onMounted(() => {
  store.getPosts();
});
</script>

<style scoped>
.posts {
  position: relative;
  min-height: 100vh;
  overflow: hidden;
  background: radial-gradient(circle at 20% 20%, #1e3a8a 0%, #0f172a 55%, #020617 100%);
  color: #f8fafc;
  font-family: system-ui, -apple-system, "Segoe UI", sans-serif;
}

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

.content {
  position: relative;
  z-index: 5;
  max-width: 900px;
  margin: 0 auto;
  padding: 6rem 1.5rem 4rem;
  text-align: center;
}

.badge {
  display: inline-block;
  padding: 0.4rem 1rem;
  margin-bottom: 1.25rem;
  border-radius: 999px;
  background: rgba(96, 165, 250, 0.15);
  border: 1px solid rgba(96, 165, 250, 0.35);
  font-size: 0.85rem;
}

.title {
  font-size: clamp(2.2rem, 5vw, 3.4rem);
  font-weight: 800;
  margin: 0 0 2.5rem;
}

.title span {
  background: linear-gradient(120deg, #60a5fa, #a78bfa, #f472b6);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.post-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 1.5rem;
  text-align: left;
}

.post-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 1rem;
  min-height: 140px;
  padding: 1.5rem;
  border-radius: 16px;
  text-decoration: none;
  color: #f8fafc;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  transition: transform 0.2s ease, box-shadow 0.25s ease, border-color 0.2s ease;
}

.post-card:hover {
  transform: translateY(-6px);
  border-color: rgba(96, 165, 250, 0.5);
  box-shadow: 0 16px 40px rgba(0, 0, 0, 0.4);
}

.post-title {
  font-size: 1.1rem;
  font-weight: 600;
  line-height: 1.4;
  margin: 0;
  text-transform: capitalize;
}

.read-more {
  font-size: 0.9rem;
  font-weight: 600;
  color: #60a5fa;
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
  animation: float 6s ease-in-out infinite;
}

.c1 {
  width: 130px;
  height: 90px;
  top: 12%;
  left: 8%;
  animation-delay: 0s;
}

.c2 {
  width: 90px;
  height: 120px;
  bottom: 12%;
  right: 10%;
  animation-delay: 1.5s;
}

.c3 {
  width: 70px;
  height: 70px;
  top: 20%;
  right: 16%;
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