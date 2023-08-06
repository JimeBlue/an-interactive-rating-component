<template>
  <div>
    <div v-if="!submitted">
      <h2>Rate us:</h2>
      <div class="stars">
        <label
          v-for="(star, index) in stars"
          :key="index"
          :for="'star_' + index"
        >
          <input
            type="radio"
            :id="'star_' + index"
            :value="index + 1"
            v-model="selectedRating"
            class="star-input"
          />
          {{ star }}
        </label>
      </div>
      <button>Submit Rating</button>
    </div>
    <div v-else>
      <h2>Thank you for your rating!</h2>
      <p>You rated us: {{ submittedRating }} stars</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      stars: ["★", "★", "★", "★", "★"],
      highlighted: -1,
      submitted: false,
      submittedRating: 0,
      selectedRating: null,
    };
  },
};
</script>
