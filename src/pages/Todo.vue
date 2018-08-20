<template>
  <div>
    <vue-element-loading :active="show" is-full-screen/>
    <div>
      <HelloWorld :message="fullName" @add="addToDo">
        <template slot="greeting">
          Hello,
        </template>
      </HelloWorld>
    </div>
    <div>
      firstname :
      <input type="text" v-model="firstName">
    </div>
    <div>
      lastname :
      <input type="text" v-model="lastName">
    </div>
    <div>
      Fullname : {{ fullName }}
    </div>
    <button @click="test">Go to test</button>
    <List/>
  </div>
</template>

<script>
import HelloWorld from '@/components/HelloWorld'
import List from '@/pages/List'
import { mapActions } from 'vuex'

export default {
  name: 'Todo',
  data () {
    return {
      firstName: '',
      lastName: '',
      show: false
    }
  },
  computed: {
    fullName () {
      return `${this.firstName} ${this.lastName}`
    }
  },
  watch: {
    firstName (newValue, oldValue) {
      // console.log('newValue = ' + newValue)
      // console.log('oldValue = ' + oldValue)
    }
  },
  methods: {
    ...mapActions({
      setList: 'setList'
    }),
    async addToDo (name) {
      this.show = true
      await this.delaySetList(name) // 3s
      this.show = false
    },
    test () {
      this.$router.push({ name: 'Test', params: { id: 100 } })
    },
    delaySetList (name) {
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          this.setList(name)
          resolve()
        }, 3000)
      })
    }
  },
  components: {
    HelloWorld,
    List
  },
  created () {
    console.log('created working...')
  },
  mounted () {
    console.log('mounted working...')
  }
}
</script>

<style scoped>
</style>
