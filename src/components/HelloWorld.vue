<template>
  <div class="hello">
    <h1>
      <slot name="greeting">
      </slot>
      {{ message }}
    </h1>
    <button @click="callEmit">Reverse</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    message: {
      type: String,
      required: true
    }
  },
  methods: {
    callEmit () {
      const splitMessage = this.message.split(' ')
      const newMessage = splitMessage[1] + ' ' + splitMessage[0]
      this.$emit('add', newMessage)
    }
  },
  created () {
    console.log('hello world created event !!!!')
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
