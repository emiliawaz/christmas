<template>
  <div class="v-home">
    <h1 class="v-home__heading">Christmas gifts</h1>
    <div class="v-home__form">
      <adding-form @new-name-added="addName"/>
      <p class="v-home__warning" v-show="doesNameExist">Warning: Person with this name is already added. Try again.</p>
    </div>
    <list :list="people" title="People"/>
    <p class="v-home__warning" v-show="people.length % 2">Warning: The number of people is odd, there is a chance of one incomplete pair.</p>
    <button class="v-home__button" @click="drawPairs()">Draw pairs</button>
    <list :list="pairs" :isPink="true" title="Pairs"/>
  </div>
</template>

<script>
import List from '@/components/List.vue'
import AddingForm from '@/components/AddingForm.vue'

export default {
  name: 'home',

  components: {
    'list': List,
    'adding-form': AddingForm
  },

  data() {
    return {
      people: [],
      peopleArray: [],
      pairs: [],
      doesNameExist: false
    }
  },

  methods: {
    addName(name) {
      if(this.people.indexOf(name) > -1) {
        this.doesNameExist = true
      } else {
        this.people.push(name)
        this.doesNameExist = false
      }
    },

    drawPairs() {
      this.pairs = []
      this.peopleArray = []
      this.peopleArray = [...this.people]

      this.people.forEach((person) => {
        this.pairs.push(`${person} buys present for ${this.pair(person)}`)
      })
    },

    pair(person) {
      let name

      name = this.peopleArray.filter(item => item !== person)
      name = name[Math.floor(Math.random() * name.length)]
      this.peopleArray.splice(this.peopleArray.indexOf(name), 1)

      return name ? name : 'nobody :('
    }
  }
}
</script>

<style lang="scss">
.v-home {
  text-align: center;
  padding: 3rem;
}

.v-home__heading {
  font-size: 4rem;
  text-align: center;
  margin: 0;
  font-weight: normal;
}

.v-home__form {
  display: block;
}

.v-home__warning {
  font-size: 1.5rem;
  color: #ff256e;
}

.v-home__button {
  display: block;
  background: #ff256e;
  color: #fff;
  font-size: 2rem;
  padding: 1rem 2rem;
  border: 0;
  border-radius: .7rem;
  cursor: pointer;
  margin: auto;

  &:hover {
    background: #d4205c;
  }
}
</style>