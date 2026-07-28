<template>
  <div class="about">
    <button class="back-btn" @click="router.push('/')" aria-label="Back to Welcome">
      <svg viewBox="0 0 24 24" width="22" height="22" fill="none" stroke="currentColor" stroke-width="2"
        stroke-linecap="round" stroke-linejoin="round">
        <line x1="19" y1="12" x2="5" y2="12" />
        <polyline points="12 19 5 12 12 5" />
      </svg>
    </button>

    <main class="content">
      <span class="badge">📮 About Posts Hub</span>
      <h1 class="title">About <span>Us</span></h1>
      <p class="intro">
        Posts Hub is a place to discover, read, and share stories from around the
        world. Browse a live feed of posts, dive into any article with its author
        and comments, and publish your own — all in a fast, clean Vue experience.
      </p>


      <h2 class="section-heading">Meet the Authors</h2>
      <div class="authors">
        <article v-for="author in authors" :key="author.name" class="author-card">
          <div class="avatar">{{ author.initials }}</div>
          <h3 class="author-name">{{ author.name }}</h3>
          <p class="author-role">{{ author.role }}</p>

          <div class="socials">
            <a :href="author.linkedin" target="_blank" rel="noopener" class="social" aria-label="LinkedIn">

              <svg viewBox="0 0 24 24" width="18" height="18" fill="currentColor">
                <path
                  d="M4.98 3.5C4.98 4.88 3.87 6 2.5 6S0 4.88 0 3.5 1.12 1 2.5 1s2.48 1.12 2.48 2.5zM.24 8h4.52v14H.24V8zm7.5 0h4.33v1.9h.06c.6-1.14 2.07-2.34 4.26-2.34 4.56 0 5.4 3 5.4 6.9V22h-4.52v-6.63c0-1.58-.03-3.6-2.2-3.6-2.2 0-2.54 1.72-2.54 3.5V22H7.74V8z" />
              </svg>
            </a>
            <a :href="`mailto:${author.email}`" class="social" aria-label="Email">

              <svg viewBox="0 0 24 24" width="18" height="18" fill="none" stroke="currentColor" stroke-width="2"
                stroke-linecap="round" stroke-linejoin="round">
                <rect x="2" y="4" width="20" height="16" rx="2" />
                <path d="m22 6-10 7L2 6" />
              </svg>
            </a>
            <a :href="author.facebook" target="_blank" rel="noopener" class="social" aria-label="Facebook">

              <svg viewBox="0 0 24 24" width="18" height="18" fill="currentColor">
                <path
                  d="M22 12a10 10 0 1 0-11.56 9.88v-6.99H7.9V12h2.54V9.8c0-2.5 1.49-3.89 3.78-3.89 1.09 0 2.24.2 2.24.2v2.46h-1.26c-1.24 0-1.63.77-1.63 1.56V12h2.78l-.44 2.89h-2.34v6.99A10 10 0 0 0 22 12z" />
              </svg>
            </a>
          </div>
        </article>
      </div>

      <section class="contact">
        <h2 class="section-heading">Get in Touch</h2>
        <div class="contact-items">
          <a class="contact-item" href="mailto:hello@postshub.com">
            <svg viewBox="0 0 24 24" width="20" height="20" fill="none" stroke="currentColor" stroke-width="2"
              stroke-linecap="round" stroke-linejoin="round">
              <rect x="2" y="4" width="20" height="16" rx="2" />
              <path d="m22 6-10 7L2 6" />
            </svg>
            <span>hello@postshub.com</span>
          </a>
          <a class="contact-item" href="tel:+919934567890">
            <svg viewBox="0 0 24 24" width="20" height="20" fill="none" stroke="currentColor" stroke-width="2"
              stroke-linecap="round" stroke-linejoin="round">
              <path
                d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72c.13.96.36 1.9.7 2.81a2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45c.9.34 1.85.57 2.81.7A2 2 0 0 1 22 16.92z" />
            </svg>
            <span>+91 9934567890</span>
          </a>
        </div>
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
import { useRouter } from "vue-router";

const router = useRouter();

const authors = [
  {
    name: "Anu Gupta",
    initials: "AG",
    role: "Founder & Lead Developer",
    linkedin: "https://www.linkedin.com/in/anu-gupta02/",
    email: "anu.gupta@postshub.com",
    facebook: "https://facebook.com/anu-gupta02",
  },
  {
    name: "Akash Gupta",
    initials: "AG",
    role: "Content & Community Manager",
    linkedin: "https://www.linkedin.com/in/akash-gupta-40b9077b/",
    email: "akash.gupta@postshub.com",
    facebook: "https://facebook.com/akash-gupta-40b9077b",
  },
  {
    name: "Mayank Pal",
    initials: "MP",
    role: "UI / UX Designer",
    linkedin: "https://www.linkedin.com/in/mayank-pal-%F0%9F%87%AE%F0%9F%87%B3-aba739161/",
    email: "mayank.pal@postshub.com",
    facebook: "https://facebook.com/mayank-pal-aba739161",
  },
];
</script>

<style scoped>
.about {
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
  margin: 0 0 1rem;
}

.title span {
  background: linear-gradient(120deg, #60a5fa, #a78bfa, #f472b6);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.intro {
  font-size: 1.1rem;
  line-height: 1.7;
  color: #cbd5e1;
  max-width: 620px;
  margin: 0 auto 3.5rem;
}

.section-heading {
  font-size: 1.5rem;
  font-weight: 700;
  margin: 0 0 1.75rem;
}

/* Author cards */
.authors {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1.5rem;
  margin-bottom: 4rem;
}

.author-card {
  padding: 2rem 1.25rem;
  border-radius: 18px;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  transition: transform 0.2s ease, box-shadow 0.25s ease;
}

.author-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 16px 40px rgba(0, 0, 0, 0.4);
}

.avatar {
  width: 72px;
  height: 72px;
  margin: 0 auto 1rem;
  display: grid;
  place-items: center;
  border-radius: 50%;
  font-size: 1.4rem;
  font-weight: 700;
  color: #fff;
  background: linear-gradient(120deg, #3b82f6, #8b5cf6);
}

.author-name {
  font-size: 1.15rem;
  font-weight: 700;
  margin: 0 0 0.25rem;
}

.author-role {
  font-size: 0.9rem;
  color: #94a3b8;
  margin: 0 0 1.25rem;
}

.socials {
  display: flex;
  justify-content: center;
  gap: 0.6rem;
}

.social {
  display: grid;
  place-items: center;
  width: 38px;
  height: 38px;
  border-radius: 10px;
  color: #cbd5e1;
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.12);
  transition: transform 0.15s ease, background 0.2s ease, color 0.2s ease;
}

.social:hover {
  transform: translateY(-3px);
  background: linear-gradient(120deg, #3b82f6, #6366f1);
  color: #fff;
}

/* Contact */
.contact-items {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.contact-item {
  display: inline-flex;
  align-items: center;
  gap: 0.65rem;
  padding: 0.85rem 1.5rem;
  border-radius: 12px;
  color: #f8fafc;
  text-decoration: none;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.12);
  transition: transform 0.15s ease, background 0.2s ease;
}

.contact-item:hover {
  transform: translateY(-2px);
  background: rgba(255, 255, 255, 0.1);
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