<template>
  <div>
    <partials-title>PERTEMUAN SENIN</partials-title>
    <atoms-float-button @click.native="increment" />
    <atoms-card>
      <template v-slot:left>
        <h1>{{fullname}}</h1>
      </template>
      <template v-slot:right>
        <FormInput name="Firstname" :val="firstname" @value="(val)=>firstname=val" />
        <FormInput name="Lastname" :val="lastname" @value="(val)=>lastname=val" />
      </template>
    </atoms-card>
    <atoms-card></atoms-card>
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
    fullname() {
      return this.firstname + " " + this.lastname;
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