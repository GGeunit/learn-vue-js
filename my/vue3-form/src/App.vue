<template>
  <div>
    <form action="" @submit.prevent="submitForm">
      <div>
        <label for="userId">ID:</label>
        <input id="userId" type="text" v-model="username">
      </div>
      <div>
        <label for="password">PW:</label>
        <input id="password" type="text" v-model="password">
      </div>
      <button type="submit">로그인</button>
    </form>
  </div>
</template>

<script>
  // import 라이브러리이름 from '패키지이름'
  import axios from 'axios'
import { ref } from 'vue';

  export default {
    // Composition API 형태
    // data
    setup() {
      var username = ref('');
      var password = ref('');

      // methods
      var submitForm = () => {
        axios.post('https://jsonplaceholder.typicode.com/users/', {
          username: username.value,
          password: password.value
        }).then(response => {
          console.log(response)
        })
      }
      return { username, password, submitForm }
    },
  }
  // methods: {
  //   logText() {
  //     this.password
  //   }
  // }
    

    // Options API 형태
    // data() {
    //   return {
    //     username: '',
    //     password: ''
    //   }
    // },
    // methods: {
    //   submitForm() {
    //     // event.preventDefault();
    //     const data = {
    //       username: this.username,
    //       password: this.password
    //     }
    //     axios.post('https://jsonplaceholder.typicode.com/users/', data)
    //       .then(response => {
    //         console.log(response)
    //       })

    //     console.log('제출됨')
    //     this.username = '',
    //     this.password = ''
    //   }
    // }
  // }
</script>

<style scoped>

</style>