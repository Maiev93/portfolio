<template>
 <div>
   <button 
    @click="$emit('click')" 
    class="button" :class="{'button__dark': color === 'dark', 'button__light': color === 'light'}">
      {{ text }}
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
    color: {
      type: String,
      default: '',
    },
  }
}
</script>

<style lang="scss" scoped>
.button {
  font-size: 20px;
  padding: 0 10px;
  border-radius: 10px;
  &__dark {
    border: 3px solid $white;
    color: $white;
    transition: all 500ms;
    &:hover {
      color: $darkTurquoise;
      border-color: $darkTurquoise;
    }
  }
  &__light {
    border: 3px solid $darkTurquoise;
    color: $black700;
  }
  &::after {
    content: "→";
  }
}
</style>