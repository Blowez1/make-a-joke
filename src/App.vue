<template>
<div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-8 mt-4">
        <make-a-joke></make-a-joke>
      </div>
    </div>
  </div>
</template>

<script>
import makeAJoke from "./components/makeAJoke";
export default {
  name: "app",
  components: {
    "make-a-joke": makeAJoke,
  },
};
</script>
<style lang="scss">
body {
  background-color: #96c8fb;
  background-image: linear-gradient(90deg, #96c8fb 0%, #ddbdfc 74%);
  font-family: 'Press Start 2P', cursive;
}
</style>