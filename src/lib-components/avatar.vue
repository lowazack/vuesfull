<template>
    <div class="avatar">
        <img class="avatar__img"
             v-if="type === 'img'"
             :src="img"
             :alt="alt"
             :style="imgStyles"
        >
        <div
                v-if="type === 'text'"
                class="avatar__text"
                :style="textStyles"
        >
            <span>
                {{ text }}
            </span>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Avatar",
        props: {
            alt: String,
            borderRadius: String,
            type: {
                default: "img",
                type: String
            },
            size: {
                default: 80,
                type: Number,
            },
            img: String,
            text: String

        },
        computed: {
            imgStyles(){
                let imgStyle = {
                    height: `${this.size}px`,
                    width: `${this.size}px`
                }

                if (this.borderRadius) {
                    imgStyle.borderRadius = this.borderRadius
                }
                return imgStyle
            },
            textStyles(){
                let textStyle = {
                    height: `${this.size}px`,
                    width: `${this.size}px`
                }

                if (this.borderRadius) {
                    textStyle.borderRadius = this.borderRadius
                }
                return textStyle
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import "../scss/vars";
    .avatar {
        display: block;
        font-family: $font-family;

        &:last-of-type {
            margin-right: 0px;
        }

        &__img {
            object-fit: cover;
            display: flex;
        }

        &__text {
            background-color: $primary;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            span {
                display: block;
            };
        }
    }
</style>