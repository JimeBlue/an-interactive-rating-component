<template>
  <div>
    <div v-if="!submitted">
      <h2>Rate us:</h2>
      <div class="stars">
        <label
          v-for="(star, index) in stars"
          :key="index"
          :for="'star_' + index"
          @mouseover="highlightStar(index)"
          :class="{ highlight: index <= highlighted }"
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
      <button @click="submitRating">Submit Rating</button>
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
  methods: {
    highlightStar(index) {
      this.highlighted = index;
    },
    resetHighlightedStar() {
      this.highlighted = -1;
    },
    submitRating() {
      if (this.selectedRating !== null) {
        this.submitted = true;
        this.submittedRating = this.selectedRating;
      }
    },
  },
};
</script>
<style scoped>
.stars {
  cursor: pointer;
  font-size: 24px;
}

.stars label {
  display: inline-block;
}
.star-input {
  position: absolute;
  left: -9999px;
}

.stars label {
  color: #d3d3d3;
  transition: color 0.2s;
  margin-right: 5px;
}
.stars label:hover,
.stars label.highlight {
  color: #ffdd00;
}
</style>
