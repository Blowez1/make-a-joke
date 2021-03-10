<template>
  <div class="text-center">
    <h2 class="title mb-4">Make me a joke!</h2>
    <button class="btn joke--btn mb-4" @click="createJoke()">Make me a joke</button>
    <h4 class="joke__setup mb-4">{{ joke.setup }}</h4>
    <div class="d-lg-flex  justify-content-center mb-3" @click="showPunchline()">
      <h5 class="joke__answer">Punchline :</h5>

      <span class="punchline" :class="isActived()">{{ joke.punchline }}</span>
    </div>

    <p class="p">To see the Punchline Click "Punchline"</p>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      joke: {
        setup: "",
        punchline: "",
      },
      isActive: false,
    };
  },
  methods: {
    createJoke() {
      axios
        .get("https://official-joke-api.appspot.com/random_joke")
        .then((response) => (this.joke = response.data));

        this.isActive = false
    },
    isActived() {
      if (!this.isActive) {
        return "deactive";
      } else {
        return "active";
      }
    },
    showPunchline() {
      if (!this.isActive) {
        this.isActive = true;
      } else {
        this.isActive = false;
      }
    },
  },
};
</script>
<style lang="scss" scoped>
.title {
  color: #36096d;
  text-align: center;
}

.joke {
  color: #734ae8;

  &__setup {
    color: #2a2a72;
  }
}

.punchline {
  cursor: pointer;
}

.deactive {
  transform: rotate(180deg) !important;
}

.joke--btn {
  border: none;
  background-color: #734ae8;
  background-image: linear-gradient(315deg, #734ae8 0%, #89d4cf 74%);
  color: #fff;
  transition: 0.3s all;

  &:hover {
    background-color: #89d4cf;
    background-image: linear-gradient(315deg, #89d4cf 0%, #734ae8 74%);
  }
}

.p {
  font-size: 13px;
}
</style>