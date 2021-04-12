<template>
  <div>
    <h1>CLASS</h1>
    <div class="row">
      <div class="col-md-4" v-for="(item,i) in listClass" :key="i">
        <class-item :desc="item.desc" :id="i" />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      listClass: [
        { desc: "Fullstack 1" },
        { desc: "Fullstack 2" },
        { desc: "Fullstack 3" },
        { desc: "Fullstack 4" },
      ],
    };
  },
};
</script>