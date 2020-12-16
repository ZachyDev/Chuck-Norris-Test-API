<template>
  <div id="home">
        <h1>Hey I'm Chuck Norris</h1>
        <button class="btn btn-primary" @click="getRandomJoke">Random  Joke</button>
        <div class="card" style="width: 18rem;margin-left:10px;margin-top:30px;" >
            <img src="" class="card-img-top" alt="">
            <div class="card-body" v-for="joke in chuckArray" :key="joke.id">
              <h5 class="card-title"><strong>Joke</strong></h5>
              <p class="card-text">{{ joke.value }}</p>
              <a href="#" class="btn btn-primary" @click="clearJoke">Clear Joke</a>
            </div>
        </div>
  </div>
</template>

<script>
import axios  from 'axios';
export default {
  data() {
    return {
      chuckArray: [],
    }
  },
  methods: {
    getRandomJoke() {
      axios.get('https://api.chucknorris.io/jokes/random')
        .then(res => {
          console.log(res.data);
          this.chuckArray.push(res.data)
        })
        .catch(err => {
          console.log(err.message)
        })
    },
    clearJoke() {
      this.chuckArray = []
    }
  }
}
</script>

<style>

</style>