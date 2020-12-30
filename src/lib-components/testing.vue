<template>
  <button
          class="button"
          :class="{
        'button--wire': wire,
        'button--danger': danger,
        'button--warning': warning,
        'button--success': success,
        'button--info': info,
        'button--block': block
    }"
  >
    <slot></slot>
  </button>
</template>

<script>
  export default {
    name: 'Button',
    props: {
      wire: Boolean,
      danger: Boolean,
      warning: Boolean,
      success: Boolean,
      info: Boolean,
      block: Boolean
    }
  }
</script>

<style lang="scss" scoped>
  @import "../scss/vars";
  $this: ".button";
  #{$this} {
    background-color: $primary;
    color: $button-text-color;
    font-size: $button-font-size;
    padding: $button-padding;
    border: $button-border;
    border-radius: $button-border-radius;
    font-family: $font-family;
    margin-right: 10px;
    cursor: pointer;
    transition:
            background-color 300ms ease-in-out,
            border-color 300ms ease-in-out,
            color 300ms ease-in-out,
            transform 300ms ease-in-out;


    &:hover {
      background-color: darken($primary, 10);
      border-color: darken($primary, 10);
      color: $button-text-color;
      transform: translateY(-3px)
    }
    &:last-of-type {
      margin-right: 0;
    }

    @each $name, $color in $colors {
      &--#{$name}{
        background-color: $color;
        border-color: $color;

        &:hover {
          background-color: darken($color, 10);
          border-color: darken($color, 10);
          color: $button-text-color;
        }
      }
    }

    &--wire {
      background-color: transparent;
      color: $primary;
    }

    @each $name, $color in $colors {
      &--wire#{$this}--#{$name} {
        background-color: transparent;
        border-color: $color;
        color: $color;

        &:hover {
          background-color: darken($color, 10);
          border-color: darken($color, 10);
          color: $button-text-color;
        }
      }
    }

    &--block {
      display: block;
      margin: 10px 0;
      width: 100%;

    }

  }
</style>