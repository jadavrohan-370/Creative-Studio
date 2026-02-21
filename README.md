# Rohan Jadav - Creative Studio Portfolio

A high-performance, cinematic portfolio designed for a Frontend Developer, built with **Vue 3**, **TypeScript**, **GSAP**, and **Tailwind CSS v4**.

## ✨ Features

- **Cinematic Hero Section**: Interactive WebGL-powered hero background.
- **Project Showcases**: Modern grid layouts with smooth reveal animations.
- **Tech Stack**: Animated 3D-tilt cards highlighting core skills.
- **Contact Form**: Integrated with **Web3Forms** for instant email notifications.
- **Resume Download**: Direct access to professional CV from Navbar and Hero.
- **Premium Aesthetics**: Glassmorphism, neon accents, and smooth smooth-scroll integration.

## 🚀 Local Setup

1. **Clone the repository:**

   ```bash
   git clone https://github.com/jadavrohan-370/Creative-Studio.git
   cd Creative-Studio
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Configure Environment Variables:**
   Create a `.env` file in the root directory and add your Web3Forms access key:

   ```env
   VITE_WEB3FORMS_ACCESS_KEY=your_key_here
   ```

4. **Run development server:**
   ```bash
   npm run dev
   ```

## 🛠️ Tech Stack

- **Framework**: [Vue 3](https://vuejs.org/) (Composition API)
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/)
- **Animations**: [GSAP](https://greensock.com/gsap/) & [ScrollTrigger](https://greensock.com/scrolltrigger/)
- **Build Tool**: [Vite](https://vitejs.dev/)
- **Email Service**: [Web3Forms](https://web3forms.com/)

## 📦 Deployment

This project is optimized for **Vercel**.

- The `vercel.json` file handles Single Page Application (SPA) routing.
- Make sure to add `VITE_WEB3FORMS_ACCESS_KEY` to your Vercel Environment Variables.
