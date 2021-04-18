<template>
  <div class="main-sidebar">
    <aside id="sidebar-wrapper">
      <div class="sidebar-brand">
        <a href="/">Sandbox</a>
      </div>
      <div class="sidebar-brand sidebar-brand-sm">
        <a href="/">Sb</a>
      </div>
      <ul class="sidebar-menu">
        <li class="menu-header">Dashboard</li>
        <li :class="$route.path=='/'?'active':''">
          <nuxt-link class="nav-link" to="/">Sandbox</nuxt-link>
        </li>
      </ul>
    </aside>
  </div>
</template>
<script>
export default {
  asyncData() {},
  data() {
    return {
      nav: ["home", "profile", "login", "hehe", "hoho"],
    };
  },
};
</script>