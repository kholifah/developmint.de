<template>
  <div>
    <section class="min-h-screen md:min-h-750 bg-about-us flex flex-col justify-center items-center">
      <h1 class="text-center text-4xl md:text-6xl text-rains-400 capitalize mt-16 md:mt-32 mb-4 md:mb-0">
        {{ $t('about.heading') }}
      </h1>
      <h2 class="text-center text-rains-300 text-xl md:text-3xl w-4/5">
        {{ $t('about.subheading') }}
      </h2>
    </section>
    <section class="md:mx-16 my-24 bg-rains-light xl:flex">
      <TeamMember
        v-for="member in members"
        :key="member.slug"
        v-bind="member"
      />
    </section>
  </div>
</template>

<script>
import TeamMember from '~/components/about-us/TeamMember'

const members = [
  {
    slug: 'alex',
    name: 'Alexander Lichter',
    links: {
      web: 'https://www.lichter.io/?ref=developmint.de',
      twitter: 'https://twitter.com/TheAlexLichter',
      github: 'https://github.com/manniL/',
      linkedin: 'https://www.linkedin.com/in/alexanderlichter'
    }
  },
  {
    slug: 'max',
    name: 'Max Langer',
    links: {
      web: 'https://max.codes/?ref=developmint.de',
      twitter: 'https://twitter.com/mangerlahn',
      github: 'https://github.com/mangerlahn/',
      linkedin: 'https://www.linkedin.com/in/max-langer-17b133136/'
    }
  }
]

export default {
  scrollToTop: true,
  components: {
    TeamMember
  },
  setup () {
    return {
      members
    }
  },
  head () {
    return this.$createSeo('about', [{
      name: 'og:image',
      content: require('~/assets/img/bg/about-us.jpg')
    }])
  }
}
</script>

<style lang="postcss">
  .bg-about-us {
    background-image: linear-gradient(rgba(11, 7, 16, 0.6), theme('colors.rains.600')), url("~assets/img/bg/about-us_sm.jpg");
    background-size: cover;
    background-position: top;

    @screen md {
      background-image: linear-gradient(rgba(11, 7, 16, .6), rgba(11, 7, 16, .6) 80%, theme('colors.rains.600')), url("~assets/img/bg/about-us.jpg");
      background-position: top;
    }
  }
</style>
