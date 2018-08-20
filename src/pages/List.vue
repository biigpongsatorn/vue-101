<template>
  <div>
    <h1>TODOLIST</h1>
    <ul>
      <li v-for="(item, index) in list" :key="index">
        {{ index + 1 }} : {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'List',
  computed: {
    ...mapGetters({
      list: 'getList'
    })
  }
}
</script>
