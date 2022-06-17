<template>
  <div>
    <a name="home"></a>
    <section class="home">
      <header class="home__header">
        <p class="home__text">
          Hello! I'm <span class="home__text_highlight">Elena Kalichkina</span>.
          I'm frontend web developer.
        </p>
      </header>
      <base-button text="My projects" color="dark" @click="toProjects" />
    </section>
    <ul class="nav">
      <li
        class="nav__item"
        v-for="nav in navs"
        :key="nav"
        @click="setActiveNav(nav)"
      >
        <a
          class="nav__a"
          :class="{ nav__a_active: activeNav === nav }"
          :href="`#${nav}`"
        >
          {{ nav }}
        </a>
      </li>
    </ul>
    <a name="about"></a>
    <section class="about">
      <header class="about__header header">About</header>
      <div class="about__card">
        <div class="plus" v-for="plus in pluses" :key="plus.title">
          <p class="icon">
            <span :class="plus.icon" />
          </p>
          <h5 class="about__title">{{ plus.title }}</h5>
          <p class="about__desc">{{ plus.description }}</p>
        </div>
      </div>
      <div class="about__body">
        <div class="about__me">
          <img
            class="about__image"
            src="@/assets/profile-photo.jpg"
            alt="Photo"
          />
          <h5 class="about__title">Who am I?</h5>
          <p class="about__desc">
            I'm frontend developer in Tomsk, Russia. Pay attention on UI/UX. I
            always use BEM and sincerely love JS. I actively read professional
            literature. Let's make something special!
          </p>
        </div>
        <div class="about__skills">
          <img class="about__skill" :title="skill" v-for="skill in skills" :key="skill" :src="require(`@/assets/icons/${skill}.svg`)" alt="skill" />
        </div>
      </div>
    </section>

    <a name="portfolio"></a>
    <section class="portfolio" ref="portfolio">
      Повседневная практика показывает, что консультация с широким активом
      представляет собой интересный эксперимент проверки модели развития. С
      другой стороны постоянное информационно-пропагандистское обеспечение нашей
      деятельности представляет собой интересный эксперимент проверки
      направлений прогрессивного развития. Таким образом постоянный
      количественный рост и сфера нашей активности играет важную роль в
      формировании систем массового участия. Задача организации, в особенности
      же постоянное информационно-пропагандистское обеспечение нашей
      деятельности влечет за собой процесс внедрения и модернизации новых
      предложений. Разнообразный и богатый опыт постоянное
      информационно-пропагандистское обеспечение нашей деятельности способствует
      подготовки и реализации системы обучения кадров, соответствует насущным
      потребностям. Идейные соображения высшего порядка, а также реализация
      намеченных плановых заданий позволяет выполнять важные задания по
      разработке дальнейших направлений развития. Разнообразный и богатый опыт
      постоянное информационно-пропагандистское обеспечение нашей деятельности
      способствует подготовки и реализации направлений прогрессивного развития.
      Не следует, однако забывать, что сложившаяся структура организации
      позволяет выполнять важные задания по разработке существенных финансовых и
      административных условий. Повседневная практика показывает, что
      консультация с широким активом представляет собой интересный эксперимент
      проверки модели развития. С другой стороны постоянное
      информационно-пропагандистское обеспечение нашей деятельности представляет
      собой интересный эксперимент проверки направлений прогрессивного развития.
      Таким образом постоянный количественный рост и сфера нашей активности
      играет важную роль в формировании систем массового участия. Задача
      организации, в особенности же постоянное информационно-пропагандистское
      обеспечение нашей деятельности влечет за собой процесс внедрения и
      модернизации новых предложений. Разнообразный и богатый опыт постоянное
      информационно-пропагандистское обеспечение нашей деятельности способствует
      подготовки и реализации системы обучения кадров, соответствует насущным
      потребностям. Идейные соображения высшего порядка, а также реализация
      намеченных плановых заданий позволяет выполнять важные задания по
      разработке дальнейших направлений развития. Разнообразный и богатый опыт
      постоянное информационно-пропагандистское обеспечение нашей деятельности
      способствует подготовки и реализации направлений прогрессивного развития.
      Не следует, однако забывать, что сложившаяся структура организации
      позволяет выполнять важные задания по разработке существенных финансовых и
      административных условий. Повседневная практика показывает, что
      консультация с широким активом представляет собой интересный эксперимент
      проверки модели развития. С другой стороны постоянное
      информационно-пропагандистское обеспечение нашей деятельности представляет
      собой интересный эксперимент проверки направлений прогрессивного развития.
      Таким образом постоянный количественный рост и сфера нашей активности
      играет важную роль в формировании систем массового участия. Задача
      организации, в особенности же постоянное информационно-пропагандистское
      обеспечение нашей деятельности влечет за собой процесс внедрения и
      модернизации новых предложений. Разнообразный и богатый опыт постоянное
      информационно-пропагандистское обеспечение нашей деятельности способствует
      подготовки и реализации системы обучения кадров, соответствует насущным
      потребностям. Идейные соображения высшего порядка, а также реализация
      намеченных плановых заданий позволяет выполнять важные задания по
      разработке дальнейших направлений развития. Разнообразный и богатый опыт
      постоянное информационно-пропагандистское обеспечение нашей деятельности
      способствует подготовки и реализации направлений прогрессивного развития.
      Не следует, однако забывать, что сложившаяся структура организации
      позволяет выполнять важные задания по разработке существенных финансовых и
      административных условий. Повседневная практика показывает, что
      консультация с широким активом представляет собой интересный эксперимент
      проверки модели развития. С другой стороны постоянное
      информационно-пропагандистское обеспечение нашей деятельности представляет
      собой интересный эксперимент проверки направлений прогрессивного развития.
      Таким образом постоянный количественный рост и сфера нашей активности
      играет важную роль в формировании систем массового участия. Задача
      организации, в особенности же постоянное информационно-пропагандистское
      обеспечение нашей деятельности влечет за собой процесс внедрения и
      модернизации новых предложений. Разнообразный и богатый опыт постоянное
      информационно-пропагандистское обеспечение нашей деятельности способствует
      подготовки и реализации системы обучения кадров, соответствует насущным
      потребностям. Идейные соображения высшего порядка, а также реализация
      намеченных плановых заданий позволяет выполнять важные задания по
      разработке дальнейших направлений развития. Разнообразный и богатый опыт
      постоянное информационно-пропагандистское обеспечение нашей деятельности
      способствует подготовки и реализации направлений прогрессивного развития.
      Не следует, однако забывать, что сложившаяся структура организации
      позволяет выполнять важные задания по разработке существенных финансовых и
      административных условий.
    </section>
  </div>
</template>

<script>
import BaseButton from '@/components/BaseButton.vue'
export default {
  name: 'IndexPage',
  components: {
    BaseButton,
  },
  data() {
    return {
      activeNav: 'home',
    }
  },
  mounted() {
    this.checkHeaderPosition()
  },
  computed: {
    navs() {
      return ['home', 'about', 'portfolio', 'contact']
    },
    pluses() {
      return [
        {
          icon: 'icon-clock',
          title: 'Fast',
          description:
            "Everyone likes fast load and lag free applications. It's my priority.",
        },
        {
          icon: 'icon-mobile',
          title: 'Responsive',
          description: 'My layouts will work correctly on any device.',
        },
        {
          icon: 'icon-smile',
          title: 'Intuitive',
          description: 'I like to make user friendly apps, intuitive UX/UI.',
        },
        {
          icon: 'icon-point-up',
          title: 'Dynamic',
          description:
            "Websites don't have to be static, I love making pages interactive.",
        },
      ]
    },
    skills() {
      return [
        'html',
        'css',
        'scss',
        'javascript',
        'vue',
        'nuxt',
        'figma',
        'photoshop',
      ]
    },
  },
  methods: {
    setActiveNav(nav) {
      this.activeNav = nav
    },
    checkHeaderPosition() {
      const observer = new IntersectionObserver((entries) => {
        entries.forEach((entry) => {
          if (entry.intersectionRatio > 0) {
            this.activeNav = entry.target.name
          }
        })
      })
      document.querySelectorAll('div a').forEach((a) => {
        observer.observe(a)
      })
    },
    toProjects() {
      this.$refs.portfolio.scrollIntoView()
      console.log('ref', this.$refs.portfolio)
    },
  },
}
</script>

<style lang="scss" scoped>
.home {
  font-family: 'GothamProMedium', sans-serif;
  color: $white;
  font-size: 43px;
  line-height: 48px;
  background: $black700;
  background-image: url(https://i.gifer.com/2iiH.gif);
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  &__header {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 10px;
  }
  &__text {
    max-width: 50%;
    text-align: center;
    &_highlight {
      color: $darkTurquoise;
    }
  }
}
.nav {
  font-family: 'GothamProMedium', sans-serif;
  background: $black700;
  display: flex;
  align-items: center;
  padding: 0 10%;
  position: sticky;
  top: 0px;
  &__item {
    margin: 10px 20px;
  }
  &__a {
    color: $white;
    text-decoration: none;
    text-transform: uppercase;
    font-size: 20px;
    &_active {
      color: $darkTurquoise;
    }
  }
}

.about {
  font-family: 'GothamProMedium', sans-serif;
  color: $black700;
  font-size: 16px;
  line-height: 24px;
  &__card {
    display: flex;
    justify-content: space-around;
  }
  &__image {
    width: 300px;
    height: 300px;
    object-fit: cover;
    border-radius: 50%;
  }
  &__title {
    font-size: 24px;
    font-weight: bold;
    margin: 20px 0 10px 0;
  }
  &__desc {
    text-align: center;
    max-width: 450px;
  }
  &__body {
    display: flex;
    align-items: center;
    margin: 40px 20px;
  }
  &__me{
    flex-basis: 60%;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 0 20px;
  }
  &__skills {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
  }
  &__skill {
    width: 100px;
    margin: 0 auto;
  }
}

.plus {
  margin: 20px;
  max-width: 310px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.header {
  font-size: 40px;
  width: 140px;
  padding: 10px;
  margin: 40px auto;
}
.icon {
  font-size: 53px;
  background: $darkTurquoise;
  color: $white;
  width: 95px;
  height: 95px;
  padding: 20px;
  border-radius: 50%;
}
</style>
