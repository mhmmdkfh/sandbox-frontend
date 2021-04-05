<template>
  <div>
    <partials-title>PERTEMUAN SENIN</partials-title>
    <input class="form-control" placeholder="A" v-model="a" />
    <input class="form-control" placeholder="B" v-model="b" />
    <h4 class="text-center">{{`(A : ${a}) + (B : ${b}) = ${parseInt(a)+ parseInt(b)}`}}</h4>
    <h5>{{route}}</h5>

    <input class="form-control" placeholder="A" v-model="variableA" />
    <input class="form-control" placeholder="B" v-model="variableB" />
    <h4 class="text-center">{{`(A : ${variableA}) + (B : ${variableB}) = ${parseInt(variableA)+ parseInt(variableB)}`}}</h4>

    <select v-model="dataSelect" class="custom-select">
      <option selected value="">Provinsi</option>
      <option value="1">One</option>
      <option value="2">Two</option>
      <option value="3">Three</option>
    </select>
    <h4 class="text-center">{{dataSelect}}</h4>

    <select v-model="dataSelect2" class="custom-select">
      <option selected value="">Kota {{dataSelect}}</option>
      <option value="1">One</option>
      <option value="2">Two</option>
      <option value="3">Three</option>
    </select>
    <h4 class="text-center">{{dataSelect2}}</h4>

  </div>
</template>
<script>
export default {
  asyncData({
    isDev,
    route,
    store,
    env,
    params,
    query,
    req,
    res,
    redirect,
    error,
  }) {
    console.log("INI ASYNC DATA");
    return {
      route: route.path,
      variableA: 0,
      variableB: 0,
    };
  },
  data() {
    console.log("INI DATA");

    return {
      dataSelect: "",
      dataSelect2: "",
      a: 0,
      b: 0,
    };
  },
};
</script>