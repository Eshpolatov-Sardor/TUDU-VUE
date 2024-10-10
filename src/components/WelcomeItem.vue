<template>
  <div class="input-add" @submit.prevent="submit">
    <h1>Tasks: {{ newTUdulength }}</h1>
    <form>
      <input class="input" type="text" v-model="text" placeholder="Yangi tudu kiriting" />
      <button class="button" type="submit">+ add</button>
    </form>
    <div class="clear-methed">
      <span class="clear-beznes "><input type="radio" value="Beznes" v-model="selectedCategory"/>Beznes</span>
      <span class="clear-market"><input type="radio" value="Market" v-model="selectedCategory"/>Market</span>
      <span class="clear-compeleted pi pi-check" @click="clearComleted"
        >Clear Completed</span
      >
      <span class="clear-all fa fa-trash" @click="clearAll">Clear all</span>
    </div>
    <ol>
      <li v-for="(item, index) in newTudu" :key="index">
        <p>{{ item.text }}</p>
        <span
          >
          <button>({{ item.category }})</button>
          <button @click="editTudu(index)">edit</button>
          <button @click="clearTudu(index)">X</button></span
        >
      </li>
    </ol>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: "",
      newTudu: [],
      selectedCategory: '',
    };
  },
  computed: {
    newTUdulength() {
      return this.newTudu.length;
    },
  },
  methods: {
    submit() {
      if (this.text !== "" && this.selectedCategory !== "") {
        const tuduList = {
          text: this.text,
          category: this.selectedCategory
        };
        this.newTudu.push(tuduList);
        localStorage.setItem(this.text, tuduList);
        if (localStorage.getItem(this.text)) {
            alert(this.text);
        } else {
            alert('Hech qanday ma\'lumot topilmadi.');
        }
        this.text = "";
        this.selectedCategory = '';
      }
    },
    clearTudu(index) {
      this.newTudu.splice(index, 1);
    },
    clearAll() {
      this.newTudu = [];
    },
    editTudu(index) {
      const newText = prompt(
        "tuxni uzgartirmoqchisiz",
        this.newTudu[index].text
      );
      if (newText !== null && newText !== "") {
        this.newTudu[index].text = newText;
      }
    },
    clearBeznes(){
    }
  },
};
</script>

<style scoped>
.input-add {
  padding: 20px;
}
</style>
