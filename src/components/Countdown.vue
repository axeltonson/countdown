<template>
  <div class="countdown__wrapper">
    <div class="countdown">
      <div class="block" v-if="years > 0">
        <p class="digit">{{ years | twoDigits }}</p>
        <p class="text">Année</p>
      </div>
      <div class="block" v-if="months > 0">
        <p class="digit">{{ months | twoDigits }}</p>
        <p class="text">Mois</p>
      </div>
      <div class="block" v-if="days > 0">
        <p class="digit">{{ days | twoDigits }}</p>
        <p class="text">Jours</p>
      </div>
      <div class="block">
        <p class="digit">{{ hours | twoDigits }}</p>
        <p class="text">Heures</p>
      </div>
      <div class="block">
        <p class="digit">{{ minutes | twoDigits }}</p>
        <p class="text">Minutes</p>
      </div>
      <div class="block">
        <p class="digit">{{ seconds | twoDigits }}</p>
        <p class="text">Secondes</p>
      </div>
    </div>
    <div class="circles__wrapper">
      <circles/>
    </div>
  </div>
</template>

<script>
import moment from 'moment'
// eslint-disable-next-line
import momentPreciseRangePlugin from 'moment-precise-range-plugin'
import Circles from '@/components/Circles'

export default {
  name: 'CountDown',
  data () {
    return {
      now: moment()
    }
  },
  components: {
    Circles
  },
  mounted () {
    window.setInterval(() => {
      this.now = moment()
    }, 1000)
  },
  props: {
    date: {
      type: String
    }
  },
  computed: {
    result () {
      return moment.preciseDiff(this.now, this.endDate, true)
    },
    endDate () {
      return moment(this.date, 'DD-MM-YYYY-HH-mm')
    },
    seconds () {
      return this.result.seconds
    },
    minutes () {
      return this.result.minutes
    },
    hours () {
      return this.result.hours
    },
    days () {
      return this.result.days
    },
    months () {
      return this.result.months
    },
    years () {
      return this.result.years
    }
  },
  filters: {
    twoDigits: function (value) {
      if (value.toString().length <= 1) {
        return '0' + value.toString()
      } else {
        return value.toString()
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  .countdown {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    z-index: 1;
    @media #{$mobile} {
      flex-direction: column;
    }
  }
  .block {
    display: flex;
    flex-direction: column;
    margin: 20px;
    @media #{$mobile} {
      margin: 10px;
    }
  }
  .text {
    color: #3CBBB1;
    text-transform: uppercase;
    font-size: 1.5rem;
    font-weight: 300;
    text-align: center;
    margin: 10px 0 0;
    @media #{$mobile} {
      margin: 0;
    }
  }
  .digit {
    color: #C4CBCA;
    font-size: 5rem;
    font-weight: 200;
    text-align: center;
  }
.circles__wrapper {
  width: 100%;
  height: 100vh;
  overflow: hidden;
  position: absolute;
  top: 0;
}
</style>
