<template>
  <nav class="navbar navbar-dark bg-dark">
    <div class="container-fluid">
      <a href="#" class="navbar-brand">Marvel</a>
      <form class="d-flex">
        <input
          type="search"
          placeholder="Поиск..."
          aria-label="Search"
          class="form-control me-2"
        />
        <button type="reset" class="btn btn-outline-light">
          все
        </button>
      </form>
    </div>
  </nav>
</template>

<script>
export default {
  name: "AppHeader",
  data() {
    return {};
  },
};
</script>

<style scoped></style>
