<template>
  <div>
    <partials-title>PERTEMUAN SENIN</partials-title>
    <center>{{i}}</center>
    <center>{{cobaPublish()}}</center>
    <hr>
    <form-input name="Nama" :val="fullname" @value="(val)=>this.fullname=val" />
    {{fullname}}
    <hr>
    <input type="text" class="form-control" v-model="fullname">
    {{firstname}}
    <br>
    {{lastname}}
    <hr>
    <input type="text" class="form-control" v-model="question">
    <p>{{ answer }}</p>

    <atoms-float-button @click.native="increment" />
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      i: 0,
      books: ["vue 1", "vue 2", "vue 3"],
      firstname: "Ghany",
      lastname: "Ersa",
      question: "",
      answer: "Questions usually contain a question mark. ;-)",
    };
  },
  watch: {
    // whenever question changes, this function will run
    question(newQuestion, oldQuestion) {
      if (newQuestion.indexOf("?") > -1) {
        this.getAnswer();
      }
    },
  },
  computed: {
    getBookPublish() {
      this.increment();
      return this.i > 3 ? "yes" : "no";
    },
    fullname: {
      get() {
        if (!this.firstname && !this.lastname) return "";
        return this.firstname + " " + this.lastname;
      },
      set(value) {
        const names = value.split(" ");
        this.firstname = names[0];
        this.lastname = names[names.length - 1];
      },
    },
  },
  methods: {
    increment() {
      this.i++;
    },
    cobaPublish() {
      return this.i > 3 ? "yes" : "no";
    },
    getAnswer() {
      this.answer = "Thinking...";
      axios
        .get("https://yesno.wtf/api")
        .then((response) => {
          this.answer = response.data.answer;
        })
        .catch((error) => {
          this.answer = "Error! Could not reach the API. " + error;
        });
    },
  },
};
</script>