<template>
  <div class="modal-wrapper" v-if="project">
    <div class="modal">
      <div class="slides">
        <div class="slide" v-for="(media, index) in project.medias" :key="media">
          <img
            class="slide__Slide none"
            :class="{block: activeSlide === index + 1}"
            :src="require(`@/assets/img/${media}.jpg`)"
            alt="project"
          />
        </div>
        <a v-if="project.medias.length > 1" class="prev" @click="plusSlides(-1)">&#10094;</a>
        <a v-if="project.medias.length > 1" class="next" @click="plusSlides(1)">&#10095;</a>
      </div>
      <!-- <ssr-carousel loop show-arrows>
        <div class="slide" v-for="media in project.medias" :key="media">
          <img
            class="modal__Slide"
            :src="require(`@/assets/img/${media}.jpg`)"
            alt="project"
          />
        </div>
      </ssr-carousel> -->
      <div class="modal__info">
        <h5 class="modal__title">{{ project.title }}</h5>
        <p v-if="project.subtitle" class="modal__subtitle">
          {{ project.subtitle }}
        </p>
        <p class="modal__description">{{ project.description }}</p>
        <div class="modal__controllers">
          <div class="modal__buttons">
            <BaseButton
              v-if="project.site"
              :link="project.site"
              class="modal__button"
              text="View site"
              color="borderless"
            />
            <BaseButton
              v-if="project.github"
              :link="project.github"
              class="modal__button"
              text="View github"
              color="black"
            />
          </div>
          <div class="modal__close" @click="refreshActiveSlide">🞫</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BaseButton from '@/components/BaseButton.vue'

export default {
  name: 'Modal',
  props: {
    project: {
      type: Object,
      default: () => {},
    },
  },
  components: {
    BaseButton,
  },
  data() {
    return {
      activeSlide: 1,
    }
  },
  methods: {
    plusSlides(index) {
      this.loopSlides(this.activeSlide += index);
    },
    loopSlides(index) {
      const {project} = this;
      if (index > project.medias.length) {this.activeSlide = 1};
      if (index < 1) {this.activeSlide = project.medias.length};
    },
    refreshActiveSlide() {
      this.activeSlide = 1;
      this.$emit("click");
    }
  }
}
</script>

<style lang="scss" scoped>
.modal-wrapper {
  background: rgba(105, 105, 105, 0.5);
  width: 100vw;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal {
  width: 700px;
  height: 700px;
  background: $white;
  box-shadow: 0 0 10px rgb(0 0 0 / 40%);
  @include text-simple;
  @include normal-font-size;
  color: $black700;
  font-size: 14px;
  &__info {
    padding: 30px;
  }
  &__title {
    font-size: 29px;
  }
  &__subtitle {
    text-transform: uppercase;
    color: $gray;
    padding: 10px 0 15px 0;
    border-bottom: 1px solid $lightGray;
  }
  &__description {
    margin: 15px 0;
  }
  &__controllers {
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
  }
  &__buttons {
    display: flex;
  }
  &__button {
    margin-right: 10px;
  }
  &__close {
    cursor: pointer;
    font-size: 25px;
  }
}
.slides {
  position: relative;
}
.slide {
   &__Slide {
    width: 700px;
    height: 450px;
    object-fit: cover;
  }
}
.prev,
.next {
  cursor: pointer;
  position: absolute;
  top: 50%;
  width: auto;
  padding: 16px;
  margin-top: -50px;
  color: $gray;
  font-weight: bold;
  font-size: 20px;
  border-radius: 0 3px 3px 0;
  user-select: none;
}

.next {
  right: 0;
  border-radius: 3px 0 0 3px;
}

.prev:hover,
.next:hover {
  background-color: rgba(0, 0, 0, 0.8);
}
.none {
  display: none;
}
.block {
  display: block;
}
</style>