<template>
  <div id="app">
      <h1>Monty Hall Problem</h1>
      <div class="form">
          <div v-if="!started">
              <label for="portsAmount">How many doors would you like to play with?</label>
              <input type="text" id="portsAmount" size="3"
                  v-model.number="portsAmount">
          </div>
          <div v-if="!started">
              <label for="selectedPort">What door do you choose to be the prize door? </label>
              <input type="text" id="selectedPort" size="3"
                  v-model.number="selectedPort">
          </div>
          <button v-if="!started" @click="started = true">Start</button>
          <button v-if="started" @click="started = false">Restart</button>
      </div>
      <div class="doors" v-if="started">
          <div v-for="i in portsAmount" :key="i">
              <Door :hasGift="i === selectedPort" :number="i" />
          </div>
      </div>
  </div>
</template>

<script>
import Door from './components/Door'

export default {
  name: 'App',
  components: { Door },
  data: function() {
      return {
          started: false,
          portsAmount: 3,
          selectedPort: null
      }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  font-family: "Fredoka", sans-serif;
}

body {
  color: #FFF;
  background-image: radial-gradient(circle, #1a3153, #3b4770, #5c5f8d, #7f76ab, #a58fc8);
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
}

#app h1 {
  font-size: 48px;
  padding: 20px;
  margin-bottom: 60px;
}

.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 40px;
}

.form, .form input, .form button {
  margin-bottom: 10px;
  margin-left: 10px;
  font-size: 2rem;
  text-align: center;
}

.form input {
  border: none;
  border-radius: 10px;
  padding: 2px 4px;
  background-color: rgba(255, 255, 255, 0.5);
}

.form button {
  padding: 2px 20px;
  margin: 30px;
  border: none;
  border-radius: 5px;
  font-weight: 600;
  color: #1a3153;
}

.doors {
  align-self: stretch;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>