<template>
  <div class="post">
    <button class="back-btn" @click="router.push('/posts')" aria-label="Back to Posts">
      <svg viewBox="0 0 24 24" width="22" height="22" fill="none" stroke="currentColor" stroke-width="2"
        stroke-linecap="round" stroke-linejoin="round">
        <line x1="19" y1="12" x2="5" y2="12" />
        <polyline points="12 19 5 12 12 5" />
      </svg>
    </button>

    <main class="content">
      <span class="badge">📮 Post Description </span>
      <article class="post-card">
        <h1 class="post-title">{{ store.post.data.title }}</h1>
        <p class="post-body">{{ store.post.data.body }}</p>

        <div class="author-row">
          <div class="avatar">{{ store.post.user.name?.charAt(0) }}</div>
          <div>
            <span class="author-label">Written by</span>
            <p class="author-name">{{ store.post.user.name }}</p>
          </div>
        </div>
      </article>

      <section class="comments">
        <h3 class="comments-heading">
          Comments ({{ store.post.comments.length }})
        </h3>
      </section>
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
import { useRoute, useRouter } from "vue-router";
import { usePostStore } from "@/stores/post";

const route = useRoute();
const router = useRouter();
const store = usePostStore();

onMounted(() => {
  store.getSinglePost(route.params.id);
});
</script>

<style scoped>
.post {
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
  max-width: 760px;
  margin: 0 auto;
  padding: 6rem 1.5rem 4rem;
}

.badge {
  display: inline-block;
  padding: 0.4rem 1rem;
  margin-bottom: 1.5rem;
  border-radius: 999px;
  background: rgba(96, 165, 250, 0.15);
  border: 1px solid rgba(96, 165, 250, 0.35);
  font-size: 0.85rem;
}

.post-card {
  padding: 2.5rem;
  border-radius: 18px;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  margin-bottom: 2rem;
}

.post-title {
  font-size: clamp(1.8rem, 4vw, 2.6rem);
  font-weight: 800;
  line-height: 1.2;
  margin: 0 0 1.25rem;
  text-transform: capitalize;
  background: linear-gradient(120deg, #60a5fa, #a78bfa, #f472b6);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.post-body {
  font-size: 1.1rem;
  line-height: 1.8;
  color: #cbd5e1;
  margin: 0 0 2rem;
}

.author-row {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding-top: 1.5rem;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
}

.avatar {
  width: 48px;
  height: 48px;
  display: grid;
  place-items: center;
  border-radius: 50%;
  font-size: 1.1rem;
  font-weight: 700;
  color: #fff;
  background: linear-gradient(120deg, #3b82f6, #8b5cf6);
  text-transform: uppercase;
}

.author-label {
  font-size: 0.8rem;
  color: #94a3b8;
}

.author-name {
  font-size: 1.05rem;
  font-weight: 600;
  margin: 0.1rem 0 0;
}

.comments-heading {
  font-size: 1.3rem;
  font-weight: 700;
  margin: 0;
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