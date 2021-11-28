<template>
  <!-- Modal -->
  <div
    class="modal fade"
    id="exampleModal"
    tabindex="-1"
    aria-labelledby="exampleModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">{{ person.name }}</h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <img class="w-100" :src="person.thumbnail" :alt="person.name" />
          <div>
            <p class="text-muted">{{ person.modified }}</p>
            <h5>Description</h5>
            <p>{{ person.description }}</p>
            <h5>Comeks</h5>
            <ul v-for="(elPerson, idx) in person.comics" :key="idx">
              <li>{{ elPerson.name }}</li>
            </ul>
          </div>
        </div>
        <div class="modal-footer">
          <button
            type="button"
            class="btn btn-secondary"
            data-bs-dismiss="modal"
          >
            Close
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppModal",
  props: ["person"],
};
</script>

<style scoped></style>
