<template>
    <div class="modal">
        <div class="modal__bg" :class="{'modal__bg--open': open}" @click="closeModal"/>

        <div class="modal__content" :class="{'modal__content--open': open}" :style="contentStyles">
            <slot></slot>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Modal",
        props: {
          modalId: [String, Number],
            maxWidth: {
              default: 800,
                type: Number
            }
        },
        data(){
            return {
                open: false,
            }
        },
        computed: {
        contentStyles(){
            return {
                maxWidth: `${this.maxWidth}px`
            }
        }
        },
        mounted() {
            this.$root.$on('openModal', id => {
                if (id === this.modalId){
                    this.open = true;
                }
            })
        },
        methods: {
            closeModal() {
                this.open = false
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import "../scss/vars.scss";

    .modal {
        height: 100vh;
        width: 100vw;
        position: fixed;
        top: 0;
        left: 0;
        pointer-events: none;
        z-index: 10000;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;

        &__bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background-color: #000;
            opacity: 0;
            transition: opacity 200ms ease-in-out;

            &--open {
                pointer-events: all;
                cursor: pointer;
                opacity: 0.8;
            }
        }

        &__content {
            background-color: white;
            padding: 10px;
            position: relative;
            border-radius: 5px;
            opacity: 0;
            transform: translateY(-10px);
            width: calc(100% - 20px);
            transition: opacity 500ms ease-in-out, transform 500ms ease-in-out;
            &--open {
                transform: translateY(0px);
                pointer-events: all;
                cursor: pointer;
                opacity: 1;
            }
        }
    }
</style>
