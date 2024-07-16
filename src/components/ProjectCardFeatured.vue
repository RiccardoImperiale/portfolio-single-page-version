<script>
import { store } from '../store';

export default {
    name: 'ProjectCardFeatured',
    props: {
        project: Object
    },
    data() {
        return {
            store,
            imageHover: false,
            isInfo: false
        }
    },
    methods: {
        changeImageStyle(val) {
            this.imageHover = val
        },
        toggleInfoCircle() {
            this.isInfo = !this.isInfo;
        }
    }
}
</script>

<template>
    <div class="project_card" @mouseleave="isInfo = false">
        <div @mouseover="changeImageStyle(true)" @mouseleave="changeImageStyle(false)" class="btn_container">
            <button class="btn" @mouseover="store.isCursorHidden = true" @mouseleave="store.isCursorHidden = false">
                <div class="logo">
                    <img width="25" src="/img/logo-gray100.png" alt="logo">
                </div>
                <div class="btn_in">
                    <a v-if="project.liveLink" :href="project.liveLink" class="text_left" target="_blank">Live
                        Version</a>
                    <a v-else :href="project.liveLink" class="text_left not_available" target="_blank">Live
                        Version</a>



                    <a :href="project.sourceLink" class="text_right" target="_blank">Source
                        Code</a>
                </div>
            </button>
        </div>
        <div @click="toggleInfoCircle" @mouseover="store.isCursorHidden = true"
            @mouseleave="store.isCursorHidden = false" class="info_btn">
            <div class="head">
                <img v-if="!isInfo" width="18" src="/img/eye-open.png" alt="eye icon">
                <img v-else width="18" src="/img/eye-close.png" alt="eye icon">
            </div>
        </div>
        <div :style="{ width: isInfo ? '110%' : '0' }" class="info_circle no_select">
            <div class="info_text">
                <div class="title">
                    <span>{{ project.title }}</span>
                </div>
                <div class="dot"></div>
                <div class="desc">
                    <p>{{ project.description }}</p>
                </div>
            </div>
        </div>
        <img :class="{ imageHover: imageHover }" class="project_image" :src="project.src" alt="project cover image">
    </div>
</template>

<style scoped>
.info_circle {
    /* background-color: rgba(255, 255, 255, 0.593);
    backdrop-filter: blur(5px);
    -webkit-backdrop-filter: blur(5px); */
    background-color: var(--pf-gray-100);
    width: 100px;
    aspect-ratio: 1;
    border-radius: 50%;
    overflow: hidden;
    position: absolute;
    bottom: 3rem;
    transform: translateY(calc(50% - 17.5px));
    z-index: 2;
    transition: .3s ease;

    .info_text {
        position: absolute;
        inset: 0;
        padding: 3rem;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: start;
        gap: .8rem;

        .title {
            color: var(--pf-gray-700);
            font-weight: 700;
            font-size: 1.2rem;
            width: 50%;
            text-align: center;
        }

        .dot {
            background-color: var(--pf-accent-b);
            width: 5px;
            height: 5px;
            border-radius: 50%;
        }

        .desc {
            color: var(--pf-gray-300);
            text-align: center;
            font-size: .9rem;
            width: 70%;
        }
    }
}

.info_btn {
    position: absolute;
    /* width: 100%; */
    bottom: 3rem;
    border-radius: 50%;
    z-index: 3;
    text-align: center;
    cursor: pointer;

    .head {
        width: 35px;
        aspect-ratio: 1;
        border-radius: 50%;
        margin: auto;
        background-color: var(--pf-accent);
        color: var(--pf-gray-100);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 1.5rem;
    }
}


.project_card {
    display: block;
    width: 100%;
    aspect-ratio: 1;
    border-radius: .25rem;
    z-index: 1;
    overflow: hidden;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;

    .btn_container {
        position: absolute;
        inset: 0;
        display: flex;
        align-items: center;
        z-index: 2;
    }

    .btn {
        cursor: default;
        width: 75px;
        height: 75px;
        border-radius: 75px;
        border: none;
        transition: .45s ease;
        overflow: hidden;
        position: relative;
        background-color: var(--pf-gray-100);

        .logo {
            top: 0;
            position: absolute;
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            filter: invert();

            & img {
                margin-bottom: 5px;
            }
        }

        .btn_in {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 4.25rem;
            transform: translateX(-16px);
            transition: .3s ease;

            a {
                text-decoration: none;
            }

            .text_left,
            .text_right {
                font-family: "Syne", sans-serif;
                white-space: nowrap;
                letter-spacing: .25px;
                font-size: 1rem;
                color: var(--pf-gray-300);
                cursor: pointer;
                transition: .25s ease;
                position: relative;

                &:hover {
                    color: var(--pf-gray-800);

                    &::after {
                        opacity: 1;
                        transition: .5s ease;
                    }
                }

                &::after {
                    content: '';
                    width: 5px;
                    height: 5px;
                    border-radius: 50%;
                    background-color: var(--pf-accent-b);
                    background-color: var(--pf-gray-600);
                    position: absolute;
                    bottom: -8px;
                    margin: auto;
                    right: 0;
                    left: 0;
                    opacity: 0;
                }
            }

            .text_left {
                transform: translateX(-150px);
            }

            .text_right {
                transform: translateX(150px);
            }

            .not_available {
                text-decoration: line-through;
                pointer-events: none;
                cursor: default;
                color: var(--pf-gray-200);
            }

        }

        &:hover {
            width: 325px;
            background-color: var(--pf-gray-100);

            /* background: rgba(233, 233, 233, 0.345);
            backdrop-filter: blur(3px);
            -webkit-backdrop-filter: blur(2px); */
            z-index: 0;
        }

        &:hover .btn_in {
            transform: translateX(0px);
        }

        &:hover .btn_in .text_left {
            transform: translateX(0);
        }

        &:hover .btn_in .text_right {
            transform: translateX(0);
        }
    }
}

.project_image {
    width: 100%;
    height: 100%;
    aspect-ratio: 1;
    object-fit: cover;
    object-position: top;
    display: block;
    filter: brightness(0.6);
    transition: transform .5s ease, filter .5s ease;
}

.imageHover {
    transform: scale(1.2) rotate(-10deg);
    filter: brightness(1);
}
</style>
