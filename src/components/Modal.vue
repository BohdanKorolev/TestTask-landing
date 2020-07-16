<template>
  <div class="modal fade show"
       tabindex="-1"
       role="dialog"
       aria-labelledby="exampleModalCenterTitle"
       aria-hidden="true">
    <div class="modal-dialog modal-dialog-centered" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title mockup-heading2">Congratulations </h5>
          <button type="button"
                  class="close"
                  aria-label="Close"
                  @click="$emit('close')">
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body">
          <p class="mockup-p">
            {{message}}
          </p>
        </div>
        <div class="modal-footer">
          <button type="button"
                  class="btn btn-danger mockup-button"
                  @click="$emit('close')">Close</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
      name: "Modal",
      props:['message'],
    }
</script>

<style scoped>
  .show {
    display: block;
    overflow: hidden;
    background-color: #00000080;
  }
</style>
