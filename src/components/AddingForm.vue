<template>
  <div class="c-adding-form">
    <label class="c-adding-form__label" for="name">Add new person to the list</label>
    <input class="c-adding-form__input" type="text" id="name" v-model="newName"/>
    <button class="c-adding-form__button" @click="$emit('new-name-added', newName)">ADD</button>
  </div>
</template>

<script>
export default {
  name: 'adding-form',

  data() {
    return {
      newName: ''
    }
  }
}
</script>

<style scoped>
.c-adding-form {
  background: rgba(255, 255, 255, 0.521);
  margin: 3rem auto;
  padding: 2rem 3rem;
  display: block;
  border-radius: .7rem;
  display: inline-block;
}

.c-adding-form__label {
  display: block;
  font-size: 2rem;
  padding: 0 1rem 1rem;
}

.c-adding-form__input {
  font-size: 1.5rem;
  padding: .5rem 1rem;
  border: 0;
  border-radius: .5rem;
  border: 1px solid #919191;
}

.c-adding-form__button {
  background: #ff256e;
  color: #fff;
  font-size: 1.5rem;
  padding: .5rem 1rem;
  border: 0;
  border-radius: .5rem;
  cursor: pointer;
  margin-left: 1rem;
}
</style>