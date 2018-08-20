<template>
  <div>Test {{ id }}</div>
</template>

<script>
export default {
  name: 'Test',
  data () {
    return {
      id: ''
    }
  },
  created () {
    console.log(this.$route)
    const id = this.$route.params.id
    this.id = id
  }
}
</script>
