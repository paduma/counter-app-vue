<template>
  <div>
    <h2 :class="getBadgeClasses()">{{ formatCount() }}</h2>
    <button class="btn btn-secondary btn-sm" @click="handlerIncrement()">Increment</button>
    <button class="btn btn-danger btn-sm m-2" @click="deleteCounter(counter.id)">Delete</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      count: this.counter.value
    }
  },
  props: {
    counter: Object,
    deleteCounter: Function
  },
  methods: {
    formatCount () {
      return this.count === 0 ? 'Zero' : this.count
    },
    getBadgeClasses () {
      let classes = 'badge m-2 badge-'
      classes += this.count === 0 ? 'warning' : 'primary'

      return classes
    },
    handlerIncrement () {
      return this.count++
    }
  }
}
</script>
