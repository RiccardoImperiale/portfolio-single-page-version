<script>
import AppHeader from './components/AppHeader.vue'
import CustomCursor from './components/CustomCursor.vue'
import AppHero from './components/AppHero.vue'
import SectionAbout from './components/SectionAbout.vue'
import SectionWorks from './components/SectionWorks.vue'
import AnimationEnd from './components/AnimationEnd.vue'
import SectionContact from './components/SectionContact.vue'

export default {
    name: 'App',
    components: {
        AppHeader,
        CustomCursor,
        AppHero,
        SectionAbout,
        SectionWorks,
        AnimationEnd,
        SectionContact
    },
}
</script>

<template>
    <AppHeader />
    <AppHero />
    <SectionAbout />
    <AnimationEnd />
    <SectionWorks />
    <SectionContact />


    <CustomCursor />
</template>

<style scoped></style>