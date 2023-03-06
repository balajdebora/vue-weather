<template>
  <div class="info">
    <img src="../static/assets/alert.png" alt="alert" />
    <h2>We're sorry, but the location you've entered cannot be found.</h2>
  </div>
</template>

<script>
export default {
  name: "ModalBox",
  props: ["error"],
};
</script>
