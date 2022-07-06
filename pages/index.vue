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
      <BaseButton text="My projects" color="dark" @click="toProjects" />
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
          <img
            class="about__skill"
            :title="skill"
            v-for="skill in skills"
            :key="skill"
            :src="require(`@/assets/icons/${skill}.svg`)"
            alt="skill"
          />
        </div>
      </div>
    </section>

    <a name="portfolio" ref="portfolio"></a>
    <section class="portfolio">
      <header class="portfolio__header header">Projects</header>
      <div class="portfolio__projects">
        <div
          class="portfolio__project project"
          v-for="project in projects"
          :key="project.title"
        >
          <img
            class="project__image"
            v-if="project.medias.length > 0"
            :src="require(`@/assets/img/${project.medias[0]}.jpg`)"
            alt="project"
          />
          <div class="project__info">
            <p class="project__name">{{ project.title }}</p>
            <p class="project__stack">{{ project.stack }}</p>
            <BaseButton
              text="View more"
              color="light"
              @click="openModal(project)"
            />
          </div>
        </div>
        <Modal
          :project="currentProject"
          @click="closeModal"
          :class="{ none: !isModalOpened }"
        />
      </div>
    </section>

    <a name="contact"></a>
    <section class="contact">
      <header class="contact__header header">Contact</header>
      <ul class="contact__medias">
        <li v-for="media in medias" :key="media.icon" class="contact__media">
          <a class="contact__link" target="_blank" :href="media.link"><span :class="media.icon" /></a>
        </li>
      </ul>
      <BaseButton color="borderless">
        <span @click="toTop">&#11165;</span>
      </BaseButton>
      <p class="contact__text">elena kalichkina <span class="contact__copy">© 2022</span></p>
    </section>
  </div>
</template>

<script>
import BaseButton from '@/components/BaseButton.vue'
import Modal from '@/components/Modal.vue'

export default {
  name: 'IndexPage',
  components: {
    BaseButton,
    Modal,
  },
  data() {
    return {
      activeNav: 'home',
      isModalOpened: false,
      currentProject: null,
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
    projects() {
      return [
        {
          title: 'WorkQuest',
          stack: 'Nuxt, Web3',
          subtitle: 'marketplace',
          description:
            'Global end-to-end jobs marketplace, powered on smart-contracts',
          medias: ['wq1', 'wq2', 'wq3', 'wq4'],
          github: 'https://github.com/WorkQuest',
          site: 'https://workquest.co/',
        },
        {
          title: 'Invest',
          stack: 'Nuxt, TS, Web3',
          subtitle: 'Invest platform',
          description:
            'Invest platform with different patterns for investment, powered on smart-contracts',
          medias: ['in1'],
        },
        {
          title: 'ArtCrypt',
          stack: 'Nuxt, Web3',
          subtitle: 'marketplace',
          description:
            'The eco-friendly NFT marketplace, based on Binance Smart Chain',
          medias: ['ac1'],
        },
        {
          title: 'Crypto wallet',
          stack: 'Vue, Web3',
          subtitle: 'wallet',
          description: 'Wallet for basic BC actions',
          medias: ['wallet1', 'wallet2'],
        },
        {
          title: 'Smart Academy Management',
          stack: 'Vue',
          subtitle: 'CRM',
          description: 'CRM for employees of Smart academy - MVP',
          medias: ['sam', 'sam1', 'sam2'],
        },
        {
          title: 'StarWars',
          stack: 'Vue, Vuetify',
          subtitle: 'Viewer',

          description: 'StarWars heroes with adding in favorites and search',
          medias: ['sw1'],
          github: 'https://github.com/Maiev93/StarWars-Vue.js',
        },
        {
          title: 'Virtual piano',
          stack: 'JS',
          subtitle: 'entertainment app',
          description: "Let's try virtual piano!",
          medias: ['vp1'],
          site: 'https://rolling-scopes-school.github.io/maiev93-JSFE2021Q1/virtual-piano/',
        },
        {
          title: 'Simon Game',
          stack: 'Vue',
          subtitle: 'game',
          description: 'A simple game for memory training',
          medias: ['sg1'],
          github: 'https://github.com/Maiev93/Simon-game',
        },
        {
          title: 'ToDo list',
          stack: 'JS',
          subtitle: 'planner',
          description: 'Just a planner with create, edit, delete items',
          medias: ['tdl1'],
          site: 'https://maiev93.github.io/clean-code-s1e1/',
          github: 'https://github.com/Maiev93/clean-code-s1e1',
        },
      ]
    },
    medias() {
      return [
        { icon: 'icon-telegram', link: 'https://t.me/Maiev' },
        {
          icon: 'icon-linkedin',
          link: 'https://www.linkedin.com/in/elena-kalichkina-8b68a61b6/',
        },
        { icon: 'icon-github', link: 'https://github.com/Maiev93' },
        {
          icon: 'icon-envelop',
          link: 'mailto:elena.kalichkina.rho@gmail.com',
        },
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
    },
    openModal(project) {
      this.currentProject = project
      this.isModalOpened = true
    },
    closeModal() {
      this.isModalOpened = false
    },
    toTop() {
      window.scrollTo(0, 0)
    },
  },
}
</script>

<style lang="scss" scoped>
.home {
  @include text-simple;
  color: $white;
  font-size: 43px;
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
    line-height: 48px;
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
  @include text-simple;
  @include normal-font-size;
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
    text-transform: uppercase;
    font-size: 20px;
    &_active {
      color: $darkTurquoise;
    }
  }
}

.about {
  @include text-simple;
  @include normal-font-size;
  color: $black700;
  padding: 100px 20px;
  &__card {
    display: flex;
    justify-content: space-around;
    max-width: 1200px;
    margin: 0 auto;
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
  &__me {
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
.portfolio {
  @include text-simple;
  @include normal-font-size;
  color: $black700;
  background: $lightGray;
  padding: 100px 20px;
  &__projects {
    display: grid;
    grid-template-columns: repeat(auto-fit, 390px);
    justify-content: center;
  }
}
.project {
  position: relative;
  &__image {
    width: 390px;
    height: 300px;
    object-fit: cover;
    margin: 0;
  }
  &__info {
    position: absolute;
    top: 0;
    background: $white;
    width: 390px;
    height: 300px;
    text-align: center;
    padding: 70px;
    opacity: 0;
    &:hover {
      opacity: 0.9;
      transition: all 500ms;
    }
  }
  &__name {
    font-weight: bold;
    font-size: 24px;
  }
  &__stack {
    color: $darkTurquoise;
    margin-bottom: 20px;
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

.contact {
  @include text-simple;
  @include normal-font-size;
  background: $black700;
  color: $white;
  padding: 50px 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  &__medias {
    display: flex;
    justify-content: space-between;
    width: 380px;
    margin-bottom: 40px;
  }
  &__link {
    color: $white;
    font-size: 27px;
  }
  &__text {
    margin-top: 40px;
    font-size: 13px;
    text-transform: uppercase;
    color: $gray;
  }
  &__copy {
    color: $darkTurquoise;
  }
}

.header {
  font-size: 40px;
  padding: 10px;
  margin: 40px 0;
  text-transform: uppercase;
  text-align: center;
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
.none {
  display: none;
}
</style>
