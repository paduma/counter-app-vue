<template>
  <div>
    <Counter v-for="counter in counters" :key="counter.id" :counter="counter" :deleteCounter="deleteCounter" />
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
    deleteCounter (counterId) {
      this.counters = this.counters.filter(c => c.id !== counterId)
    }
  }
}
</script>