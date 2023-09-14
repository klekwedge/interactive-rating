

<template>
  <main v-show="!isVisible" class="card">
    <div class="card__container">
      <div class="card__icon">
        <img src="./assets/images/icon-star.svg" alt="icon image" />
      </div>
      <div class="text">
        <h1>How did we do?</h1>
        <p>
          Please let us know how we did with your support request. All feedback
          is appreciated to help us improve our offering!
        </p>
      </div>
      <ul>
        <li
          v-for="rate in rates"
          :key="rate"
          @click="activeRating = rate"
          class="card__rating"
          :class="{ active: activeRating === rate }"
        >
          {{ rate }}
        </li>
      </ul>

      <button :disabled="activeRating === null" @click="isVisible = !isVisible" class="card__button">
        Submit
      </button>
    </div>
  </main>
  <div v-show="isVisible">
    <Result :activeRating="activeRating" />
  </div>
</template>

<script setup>
import { ref } from "vue";
import Result from "./components/Result.vue";

const isVisible = ref(false);
const activeRating = ref(null);
const rates = ref([1, 2, 3, 4, 5]);
</script>

<style lang="scss" scoped>
@import "./style";

.card {
  display: flex;
  align-items: center;
  max-width: 26rem;
  background-image: linear-gradient(hsl(213, 19%, 18%), hsl(216, 12%, 11%));
  border-radius: 2rem;
  .card__container {
    margin: $baseMargin * 2;

    .card__icon {
      display: flex;
      align-items: center;
      justify-content: center;
      margin-bottom: $baseMargin * 2;
      background-color: hsl(213, 19%, 23%);
      width: 3rem;
      height: 3rem;
      border-radius: 50%;
    }
    .text h1 {
      font-size: 2rem;
      font-weight: 400;
    }
    .text p {
      color: $lightGray;
      margin-top: $baseMargin;
    }
    ul {
      margin-top: $baseMargin * 2;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding-left: 0;

      .card__rating {
        display: flex;
        align-items: center;
        justify-content: center;
        background-color: hsl(213, 19%, 23%);
        width: 3rem;
        height: 3rem;
        color: $lightGray;
        border-radius: 50%;
        cursor: pointer;
        &.active {
          background-color: $orange;
          color: white;
          &:hover {
            background-color: $orange;
          }
        }
        &:hover {
          background-color: $lightGray;
          color: white;
          transition: 0.4s;
        }
      }
    }
    .card__button {
      margin-top: $baseMargin * 2;
      cursor: pointer;
      text-transform: uppercase;
      color: white;
      background-color: $orange;
      border: none;
      border-radius: 3rem;
      width: 100%;
      height: 2.5rem;
      letter-spacing: 2px;
      &:hover:not(:disabled) {
        background-color: white;
        color: $orange;
        transition: 0.5s;
      }

      &:disabled {
        background-color: gray;
        cursor: not-allowed;
      }
    }
  }
}
</style>