<template>
  <div id="app">
    <!-- Render Navbar only if the current route is not DetailedBlog1 -->
    <Navbar v-if="!isAuthPage && !isDetailedBlogPage" />
    <router-view v-if="shouldShowRouterView"></router-view>
    <!-- Render sections only if the current route is not DetailedBlog1 -->
    <template v-if="shouldShowMainContent">
      <section id="intro">
        <IntroSection />
      </section>
      <section id="social-proof">
        <SocialProof />
      </section>
      <section id="features">
        <FeaturesPage />
      </section>
      <section id="process">
        <ProcessInt />
      </section>
      <section id="blog">
        <BlogPost />
      </section>
      <section id="project">
        <Project />
      </section>
      <section id="about-us">
        <AboutUs />
      </section>
      <section id="service">
        <Service />
      </section>
      <section id="questions">
        <Questions />
      </section>
      <section id="chat">
        <Chat />
      </section>
      <section id="contact">
        <ContactUs />
      </section>
    </template>

    <!-- Router view for all routes, including DetailedBlog1 -->
    <Footer v-if="!isAuthPage && !isDetailedBlogPage" />
  </div>
</template>

<script>
import Navbar from "./components/NavBar.vue";
import IntroSection from "./components/IntroSection.vue";
import SocialProof from "./components/SocialProof.vue";
import FeaturesPage from "./components/FeaturesPage.vue";
import ProcessInt from "./components/ServiceSection.vue";
import BlogPost from "./components/BlogPost.vue";
import ContactUs from "./components/ContactUs.vue";
import Footer from "./components/FooterBar.vue";
import Service from "./components/ServiceSection.vue";
import Project from "./components/ProjectSection.vue";
import AboutUs from "./components/AboutUs.vue";
import Questions from "./components/Questions.vue";
import Chat from "./components/Chat.vue";

export default {
  name: "App",
  components: {
    Navbar,
    IntroSection,
    SocialProof,
    FeaturesPage,
    ProcessInt,
    BlogPost,
    ContactUs,
    Project,
    Footer,
    Service,
    AboutUs,
    Questions,
    Chat,
  },
  computed: {
    isDetailedBlogPage() {
      return this.$route.name === "DetailedBlog1";
    },  
    isAuthPage() {
      return ['SignIn', 'SignUp'].includes(this.$route.name);
    },
    shouldShowRouterView() {
      return this.isAuthPage || this.isDetailedBlogPage;
    },
    shouldShowMainContent() {
      return !this.isAuthPage && !this.isDetailedBlogPage;
    }
  }
};
</script>

<style>
body {
  margin: 0;
  font-family: "Space Grotesk", sans-serif;
  background-color: #f3f4f6;
}
#app {
  text-align: center;
}

section {
  padding: 0; /* Adjust padding for better spacing */
}

.card {
  background: white;
  border-radius: 8px;
  padding: 1rem;
  margin: 1rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}
</style>
