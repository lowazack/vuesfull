<template>
    <article class="card">
        <a
                v-if="image"
                :target="target"
                :href="destination"

                class="card__img-cont">
            <img
                    :src="image"
                    alt=""
                    class="card__img"
            >
        </a>
        <div class="card__content">
            <a class="card__title" :href="destination" :target="target">Card</a>
            <p class="card__excerpt" :style="excerptStyles">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
        </div>
    </article>
</template>

<script>

    export default {
        name: "Card",
        props: {
            target: String,
            lineLimit: {
                default: 2,
                type: Number
            },
            destination: String,
            image: String
        },
        computed: {
            excerptStyles(){
                return {
                    '-webkit-line-clamp': this.lineLimit
                }
            }
        }
    }
</script>

<style lang="scss">
    @import "../scss/vars";

    .card {
        background-color: $card-bg-color;
        border-radius: $card-border-radius;
        overflow: hidden;
        box-shadow: 0px 2px 6px 0px rgba(0, 0, 0, 0.3);
        font-family: $font-family;
        transition: transform 300ms ease-in-out;
        &:hover {
            transform: translateY(-3px);
        }

        &__img-cont {
            display: block;
            width: 100%;
            padding-bottom: 70%;
            position: relative;
        }

        &__img {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        &__content {
            padding: 15px;
            padding-bottom: 20px;
        }

        &__title {
            margin: 0;
            font-weight: 600;
            font-size: 1.4rem;
            display: block;
            line-height: 1.3;
            margin-bottom: 0.3rem;
            color: black;
            text-decoration: none;

        }

        &__excerpt {
            margin: 0;
            display: -webkit-box;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }

    }

</style >