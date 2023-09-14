

<template>
  <main>
    <div v-show="!isVisible" class="card-container">
      <div class="content-container">
        <div class="star-icon">
          <img src="./assets/images/icon-star.svg" alt="" />
        </div>
        <div class="text">
          <h1>How did we do?</h1>
          <p>
            Please let us know how we did with your support request. All
            feedback is appreciated to help us improve our offering!
          </p>
        </div>

        <ul>
          <li
            v-for="rate in rates"
            :key="rate"
            @click="activeRef = rate"
            class="rating"
            :class="{ active: activeRef === rate }"
          >
            {{ rate }}
          </li>
        </ul>

        <button @click="isVisible = !isVisible" class="btn">Submit</button>
      </div>
    </div>
  </main>
</template>

<script setup>
import { ref } from "vue";

const isVisible = ref(false);
const activeRef = ref(null);
const rates = ref([1, 2, 3, 4, 5]);
</script>

<style lang="scss" scoped>
@import './style';
</style>