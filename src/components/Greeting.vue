<template lang="html">
  <transition
    mode="out-in"
    name="slide"
  >
    <span
      v-if="isDefault"
      key="1"
      class="slide"
    >
      Good morning,
    </span>
    <span
      v-else
      key="2"
      class="slide"
    >
      {{ greeting }},
    </span>
  </transition>
</template>

<script>
const GREETINGS = {
  en: {
    'EARLY_MORNING': 'Hello early bird',
    'MORNING': 'Good morning',
    'AFTERNOON': 'Good afternoon',
    'EVENING': 'Good evening',
  },
  pl: {
    'EARLY_MORNING': 'Dzień dobry',
    'MORNING': 'Dzień dobry',
    'AFTERNOON': 'Dzień dobry',
    'EVENING': 'Dobry wieczór'
  },
  de: {
    'EARLY_MORNING': 'Guten Morgen',
    'MORNING': 'Guten Morgen',
    'AFTERNOON': 'Guten Tag',
    'EVENING': 'Guten Abend'
  },
  es: {
    'EARLY_MORNING': 'Buenos días',
    'MORNING': 'Buenos días',
    'AFTERNOON': 'Buenas tardes',
    'EVENING': 'Buena noches'
  },
  fr: {
    'EARLY_MORNING': 'Bonjour',
    'MORNING': 'Bonjour',
    'AFTERNOON': 'Bonne après-midi',
    'EVENING': 'Bonsoir'
  },
  it: {
    'EARLY_MORNING': 'Buongiorno',
    'MORNING': 'Buongiorno',
    'AFTERNOON': 'Buon pomeriggio',
    'EVENING': 'Buonasera'
  },
  de_CH: {
    'EARLY_MORNING': 'Guete Morge',
    'MORNING': 'Guete Morge',
    'AFTERNOON': 'Guete Nami',
    'EVENING': 'Guete Abe'
  },
}

export default {
  props: {
    dayTime: {
      type: String,
      default: 'MORNING'
    },
    language: {
      type: String,
      default: 'en'
    }
  },
  computed: {
    greeting () {
      try {
        return GREETINGS[this.language][this.dayTime]
      } catch (e) {
        return GREETINGS.en[this.dayTime]
      }
    },
    isDefault () {
      return this.dayTime === 'MORNING'
    }
  }
}
</script>

<style>
.greeting {
  transition: width 0.2s;
}

.slide {
  display: inline-block;
  transition: all ease .4s;
}

.slide-enter {
  opacity: 0;
  transform: translateY(30px);
}

.slide-leave-to {
  opacity: 0;
  transform: translateY(-30px);
}
</style>
