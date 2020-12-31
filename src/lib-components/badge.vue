<template>
    <span
            class="badge"
            ref="badge"
            :style="jsStyles"
            :class="`badge--${modifier}`"
    >
       {{value}}
    </span>
</template>

<script>
    export default {
        name: "Badge",
        mounted() {
            this.isMounted = true;
        },
        props: {
            modifier: String,
            value: [Number, String]
        },
        computed: {
            jsStyles() {
                if (!this.isMounted) {
                    return {
                        borderRadius: '24px'
                    };
                }
                let height = this.$refs.badge.offsetHeight;

                height = (height * 2) / 2

                return {
                    minWidth: `${height}px`,
                    height: `${height}px`,
                    borderRadius: `${height + 3}px`
                }
            }
        },
        data() {
            return {
                isMounted: false
            }
        },

    }
</script>

<style lang="scss" scoped>
    @import "../scss/vars";

    $this: ".badge";

    #{$this} {
        background-color: $primary;
        position: absolute;
        top: 0;
        right: 0;
        transform: translate(50%, -50%);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 0.9rem;
        padding: 2px;
        font-family: $font-family;
        box-shadow: 0px 2px 6px 0px rgba(0, 0, 0, 0.3);
        line-height: 1;

        @each $name, $color in $colors {
            &--#{$name} {
                background-color: $color;
                border-color: $color;
            }
        }

    }
</style>