<template>
  <div>
    <h2 :class="getBadgeClasses()">{{ formatCount() }}</h2>
    <button class="btn btn-secondary btn-sm" @click="increment()">Increment</button>
    <button class="btn btn-danger btn-sm m-2" @click="deleteCounter()">Delete</button>
  </div>
</template>

<script>
export default {

  props: ['counter'],
  methods: {
    formatCount () {
      const { value } = this.counter
      return value === 0 ? 'Zero' : value
    },
    getBadgeClasses () {
      let classes = 'badge m-2 badge-'
      classes += this.counter.value === 0 ? 'warning' : 'primary'

      return classes
    },
    increment () {
      this.$emit('incrementEvent', this.counter)
    },
    deleteCounter () {
      this.$emit('deleteEvent', this.counter.id)
    }
  }
}
</script>
