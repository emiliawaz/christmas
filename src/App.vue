<template>
  <div class="container">
    <ul class="people">
      <div class="dropdown">
        <button
          class="btn dropdown-toggle"
          type="button"
          id="dropdownMenu2"
          data-toggle="dropdown"
          aria-haspopup="true"
          aria-expanded="false"
          @click="toggle"
        >
        <p v-if="name">{{ name }}</p>
        <p v-else>Wybierz swoje inicjały</p>
        </button>
        <div class="dropdown-menu" aria-labelledby="dropdownMenu2" id="menu">
          <button
            class="dropdown-item"
            type="button"
            v-for="(person, i) in people"
            :key="i"
            v-if="people"
            :id="i"
            @click="toggle"
          >{{ person }}</button>
        </div>
      </div>
    </ul>
    <button class="lottery" @click="randomPair()">Losuj parę!</button>
    <h2 v-if="pair">Twój prezent trafi do {{ pair }}!</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      people: ["AB", "AK", "EW", "HW", "IO", "JO", "JW", "KK", "MB", "MW", "NS", "TW"],
      name: null,
      pair: ''
    };
  },

  methods: {
    randomPair() {
      // this.pair = some random pair from this function
      console.log(this.pair);
    },
    toggle(e) {
      let el = document.getElementById('menu').classList.toggle('visible');

      if(e.currentTarget.className === 'dropdown-item') {
        this.name = e.currentTarget.innerText;
      } 
    }
  }
};
</script>

<style>
body {
  background: radial-gradient(ellipse at center, #fff 0%, #fff 10%, #ccc 10%);
  background-size: 70px 70px;
  background-repeat: repeat;
  background-position: 5px center;
  width: 100vw;
  height: 50px;
  color: #fff;
  font-size: 16px;
  font-weight: bold;
  font-family: 'Courgette', cursive;
  font-size: 25px;
}
.container {
  width: 100%;
  text-align: center;
  margin-top: 20vh;
}
ul.people {
  width: 70%;
  padding: 0;
  margin: auto;
}
li.person {
  width: 100%;
  background: #e52e27;
  list-style-type: none;
}
h2 {
  color: #e52e27;
}
button.lottery {
  background: #0b602a;
  padding: 0.3em 1em;
  border: 0;
  border-radius: 30px;
  margin: 5em 0;
  cursor: pointer;
  color: #fff;
}
.dropdown {
  position: relative;
  width: fit-content;
  margin: auto;
}
.dropdown-toggle {
  background-color: #e52e27;
  border: 0;
  color: #fff;
}
.dropdown-toggle:hover, .dropdown-toggle:active {
  background-color: #e52e27;
}
.visible {
  display: block;
}
.dropdown-menu {
  top: 36px;
  width: 100%;
  cursor: pointer;
}
.dropdown-item {
  margin: 5px 0;
}
p {
  display: inline;
  margin-right: .5em;
}
button {
  cursor: pointer;
}
</style>
