<template>
  <div>
    <a
      v-if="link !== ''"
      class="button"
      :class="btnClass"
      :href="link"
      target="_blank"
    >
      {{ text }}
    </a>
    <button v-else @click="$emit('click')" class="button" :class="btnClass">
      {{ text }}
      <slot></slot>
    </button>
  </div>
</template>

<script>
export default {
  name: 'BaseButton',
  props: {
    text: {
      type: String,
      default: '',
    },
    link: {
      type: String,
      default: '',
    },
    color: {
      type: String,
      default: '',
    },
  },
  computed: {
    btnClass() {
      const { color } = this
      return [
        { button_light: color === 'light' },
        { button_dark: color === 'dark' },
        { button_borderless: color === 'borderless' },
        { button_black: color === 'black' },
      ]
    },
  },
}
</script>

<style lang="scss" scoped>
.button {
  font-size: 20px;
  padding: 10px;
  border-radius: 10px;
  text-decoration: none;
  &_dark {
    border: 3px solid $white;
    color: $white;
    transition: all 500ms;
    &:hover {
      color: $darkTurquoise;
      border-color: $darkTurquoise;
    }
  }
  &_light {
    border: 3px solid $darkTurquoise;
    color: $black700;
    transition: all 500ms;
    &:hover {
      color: $white;
      background: $darkTurquoise;
    }
  }
  &_borderless {
    border: none;
    color: $white;
    background: $darkTurquoise;
    transition: all 500ms;
    &:hover {
      color: $darkTurquoise;
      background: $white;
    }
  }
  &_black {
    border: none;
    color: $white;
    background: $black700;
    transition: all 500ms;
    &:hover {
      color: $black700;
      background: $white;
    }
  }
  // &_up {
  //   border: none;
  //   color: $white;
  //   background: $dar;
  // }
}
</style>