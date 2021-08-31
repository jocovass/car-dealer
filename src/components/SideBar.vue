<template>
  <div class="sidebar">SideBar</div>
</template>

<style lang="scss" scoped>
@import "@/styles/_app.scss";

.sidebar {
  background-color: $accent-light;
  display: none;
}

@media only screen and (min-width: 1400px) {
  .sidebar {
    display: block;
    min-width: 330px;
  }
}
</style>
