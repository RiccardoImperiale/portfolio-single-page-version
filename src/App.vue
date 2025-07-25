<script>
import AppHeader from "./components/AppHeader.vue";
import CustomCursor from "./components/CustomCursor.vue";
import AppHero from "./components/AppHero.vue";
import SectionAbout from "./components/SectionAbout.vue";
import SectionWorks from "./components/SectionWorks.vue";
import AnimationEnd from "./components/AnimationEnd.vue";
import SectionContact from "./components/SectionContact.vue";

export default {
  name: "App",
  components: {
    AppHeader,
    CustomCursor,
    AppHero,
    SectionAbout,
    SectionWorks,
    AnimationEnd,
    SectionContact,
  },
  data() {
    return {
      loading: true,
    };
  },
  // mounted() {
  //   setTimeout(() => {
  //     this.loading = false
  //   }, 1500)
  // }
};
</script>

<template>
  <!-- <div v-if="loading" class="loader">
    <p>Loading...</p>
  </div> -->

  <div>
    <AppHeader />
    <AppHero />
    <SectionAbout />
    <AnimationEnd />
    <SectionWorks />
    <SectionContact />
    <CustomCursor />
  </div>
</template>

<style scoped>
.loader {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  background: #fff;
}
</style>
