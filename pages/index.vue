<template>
  <div class="lp-container">
    <b-img src="../assets/TaylorAndLuke.jpg" class="background-image"></b-img>
    <div class="overlay">
      <div class="form-container">
        <b-img />
        <p>$150 Off 1.5 Hour Utah Engagements</p>
        <p>Description text</p>
        <input v-model="email" type="text" />
        <button @click="submitEmail">Submit</button>
        <p>100% Secure. We Never Share Your Email test2</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LandingPage',
  data() {
    return {
      email: ''
    }
  },
  methods: {
    submitEmail() {
      this.$axios
        .post('https://photo-lead-gen.herokuapp.com/leads/new', {
          email: this.email
        })
        .then((res) => {
          console.log(res)
        })
        .catch((err) => {
          console.error(err)
        })
    }
  }
}
</script>

<style>
.lp-container {
  width: 100vw;
  height: calc(var(--vh, 1vh) * 100);
  position: relative;
}

.background-image {
  object-fit: cover;
  width: 100%;
  height: calc(var(--vh, 1vh) * 100);
}

.overlay {
  position: absolute;
  top: 0px;
  left: 0px;
  height: calc(var(--vh, 1vh) * 100);
  width: 100vw;
  display: flex;
  align-items: flex-start;
  justify-content: center;
}

.form-container {
  width: 379px;
  max-width: 100%;
  height: 90%;
  max-height: 90%;
  background-color: rgba(0, 0, 0, 0.6);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
}
</style>
