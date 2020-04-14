<template>
  <div>
    <button class="btn btn-primary btn-sm m-2" @click="reset">Reset</button>
    <Counter v-for="counter in counters" :key="counter.id" :counter="counter" @deleteEvent="deleteCounter" @incrementEvent="increment" />
  </div>
</template>

<script>
import Counter from './Counter'
export default {
  name: 'Counters',
  components: {
    Counter
  },
  data () {
    return {
      counters: [
        { id: 1, value: 4 },
        { id: 2, value: 0 },
        { id: 3, value: 0 },
        { id: 4, value: 0 }
      ]
    }
  },
  methods: {
    increment (counter) {
      const counters = this.counters
      const index = this.counters.indexOf(counter)
      counters[index] = counter
      counters[index].value++
      this.counters = counters
    },
    deleteCounter (counterId) {
      this.counters = this.counters.filter(c => c.id !== counterId)
    },
    reset () {
      const counters = this.counters.map(c => {
        c.value = 0
        return c
      })
      this.counters = counters
    }
  }
}
</script>
