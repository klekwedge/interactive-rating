

<template>
  <div class="result-container">
    <div class="result-content">
      <img src="../assets/images/illustration-thank-you.svg" alt="thank you svg" />
      <p class="result">You selected {{ activeRating }} out of 5</p>
      <h2>Thank you!</h2>
      <p class="thank-you">
        We appreciate you taking the time to give a rating. If you ever need
        more support, don't hesitate to get in touch!
      </p>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["activeRating"]);
</script>

<style lang="scss" scoped>
@import "../style";

.result-content {
  // position: absolute;
  top: 29%;
  left: 31%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  max-width: 26rem;
  background-image: linear-gradient(hsl(213, 19%, 18%), hsl(216, 12%, 11%));
  border-radius: 2rem;

  img {
    margin-top: $baseMargin * 3;
  }
  .result {
    margin-top: $baseMargin * 2;
    font-weight: 400;
    color: hsl(25, 97%, 39%);
    background-color: hsl(213, 19%, 23%);
    padding: 0.3rem 2rem;
    border-radius: 3rem;
  }
  h2 {
    margin-top: $baseMargin * 2;
    font-size: 2rem;
    font-weight: 400;
  }
  .thank-you {
    color: $lightGray;
    width: 100%;
    margin: $baseMargin;
    text-align: center;
    width: 82%;
  }
}
</style>