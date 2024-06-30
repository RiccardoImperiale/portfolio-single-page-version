<script>
import { store } from '../store.js'
import { animateHeader } from '../assets/gsap/animations.js';

export default {
    name: 'AppHeader',
    data() {
        return {
            store
        }
    },
    methods: {
        isOver(val) {
            store.isCustomCursor = val
        },
    },
    mounted() {
        // const header = this.$refs.header;
        const header = document.querySelector('header')
        const links = document.querySelectorAll('.link_container')

        animateHeader(header, links);
    },
}
</script>

<template>
    <header ref="header" @mouseover="store.isCursorHidden = true" @mouseleave="store.isCursorHidden = false">
        <nav>
            <img class="logo" width=35 src="/img/logo-wt.png" alt="logo">
            <div class="page_links">
                <div class="link_container">
                    <a href="#about">ABOUT</a>
                    <a href="#about">ABOUT</a>
                </div>
                <div class="link_container">
                    <a href="#works">WORKS</a>
                    <a href="#works">WORKS</a>
                </div>
                <div class="link_container pill">
                    <a href="#contact">CONTACT</a>
                    <a href="#contact">CONTACT</a>
                </div>
            </div>
        </nav>
    </header>
</template>

<style scoped>
header {
    position: absolute;
    top: 0;
    width: 100%;
    z-index: 10;

    & nav {
        max-width: 1920px;
        width: 90%;
        margin: auto;
        padding: 1.5rem 0;
        display: flex;
        justify-content: space-between;
        align-items: center;

        .logo {
            mix-blend-mode: color-dodge;
            opacity: 0.6;
        }

        .page_links {
            display: flex;
            align-items: center;
            gap: 1.6rem;

            a {
                display: block;
                text-decoration: none;
                color: var(--pf-gray-100);
                font-size: .9rem;
                opacity: 0.7;
                transition: .3s ease;
            }

            .link_container {
                overflow: hidden;
                height: 17px;

                &:hover a {
                    transform: translateY(-20px);
                }

                a:nth-of-type(2) {
                    padding-top: 2px;
                }
            }

            .pill {
                background-color: var(--pf-gray-700);
                padding: 1.25rem 1.5rem;
                border-radius: 20px;
                overflow: hidden;
                height: 20px;
                text-decoration: none;
                display: flex;
                flex-direction: column;

                &:hover a {
                    transform: translateY(-35px);
                }

                a {
                    transform: translateY(-8px);
                }

                a:nth-of-type(2) {
                    padding-top: 10px;
                }
            }
        }
    }
}
</style>