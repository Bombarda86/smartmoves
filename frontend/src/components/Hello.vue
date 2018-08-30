<template>
  <div class="hello">
    <img src="./../assets/spring-boot-vuejs-logo.png">
    <h1>{{ hellomsg }}</h1>
    <h2>See the sources here: </h2>
    <ul>
      <li><a href="https://github.com/jonashackt/spring-boot-vuejs" target="_blank">github.com/jonashackt/spring-boot-vuejs</a></li>
    </ul>
    <h3>This site contains more stuff :)</h3>
    <ul>
      <li>HowTo call REST-Services:</li>
      <li><router-link :to="{ name: 'Service' }" exact target="_blank">/callservice</router-link></li>
      <li>HowTo to play around with Bootstrap UI components:</li>
      <li><router-link :to="{ name: 'Bootstrap' }" exact target="_blank">/bootstrap</router-link></li>
      <li>HowTo to interact with the Spring Boot database backend:</li>
      <li><router-link :to="{ name: 'User' }" exact target="_blank">/user</router-link></li>
    </ul>

    <button class=”Search__button” @click="callRestService()">CALL Spring Boot REST backend service</button>
    <b-btn @click="callRestService()">CALL Spring Boot REST backend service</b-btn>
    <h3>{{ response }}</h3>

  </div>
</template>

<script>
  import {AXIOS} from './http-common'

  export default {
    name: 'hello',
    props: { hellomsg: { type: String, required: true } },

    data() {
      return {
        posts: [],
        errors: [],
        response: ''
      }
    },
    methods: {
      // Fetches posts when the component is created.
      callRestService (){
        AXIOS.get(`/hello`)
          .then(response => {
            // JSON responses are automatically parsed.
            this.response = response.data
            console.log(this.response)
          })
          .catch(e => {
            this.errors.push(e)
          })
      }
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
