<template>
  <div>
    this is for practice
    {{ greeting }}
    <input type="text" v-model="greeting" />
    <div v-if="count === 1">
      green
    </div>
    <div v-else-if="count === 2">
      blue
    </div>
    <div v-else>
      red
    </div>
    <div v-show="count === 1">view show</div>
    <h2>smart directives</h2>
    Sign up
    <br />
    <p v-text="email" />
    <p v-once>{{ email }}</p>
    <input type="text" v-model="email" />
    <input type="text" v-model="email" :class="{ red: email.length < 2 }" />
    <input
      type="text"
      v-model="email"
      :class="[email.length < 2 ? 'red' : 'green']"
    />
    <br />
    <button onclick="alert('sign up')" :disabled="email.length < 2">
      Submit
    </button>
    <h1>looping</h1>
    <input type="text" v-model="newCat" v-on:keyup.enter="addNewCat" />
    <button v-on:click="addNewCat">Add new cat</button>
    <ul>
      <li v-bind:key="cat" v-for="cat in cats">{{ cat }}</li>
    </ul>
    <ul>
      <li v-bind:key="cat" v-for="cat in cats">
        {{ cat | kittyFly | capitalize }}
      </li>
    </ul>
    <div>
      {{ kityfy }}
    </div>
    <CatList :cats="cats" />
  </div>
</template>

<script>
import CatList from "./CatList";
export default {
  name: "Practice",
  components: {
    CatList,
  },
  data() {
    return {
      greeting: "",
      count: 100,
      email: "email",
      cats: ["kitkat", "henry", "fish"],
      newCat: "",
    };
  },
  methods: {
    addNewCat(e) {
      e.preventDefault();
      this.cats = [...this.cats, this.newCat];
      this.newCat = "";
    },
  },
  filters: {
    capitalize(item) {
      return item.toUpperCase();
    },
    kittyFly(item) {
      return `${item}fly`;
    },
  },
  computed: {
    kityfy() {
      if (this.newCat.length > 5) {
        return `${this.newCat}y`;
      } else {
        return null;
      }
    },
  },
  created() {
    console.log("this is create");
  },
  mounted() {
    console.log("this is mounted");
  },
  destroyed() {
    console.log("this is destroyed");
  },
  updated() {
    console.log("this is updated");
  },
};
</script>

<style scoped>
.red {
  border: 2px solid red;
}

.green {
  border: 2px solid green;
}
</style>
