<template>
<div id="App">
    <h3> Example 1</h3>
    <div>Date: {{ example1 }}</div>
    <button @click="getLanguage">Get Language</button>
</div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'App',
    components: {

    },
    data () {
        return {
            example1: ''
        }
    },
    methods: {
        async getLanguage () {
            try {
                const res = await axios.post('http://localhost:4000/graphql', {
                    query: '{language}'
                })
                this.example1 = res.data.data.language
            } catch (e) {
                console.log('error >>', e)
            }
        }
    }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
