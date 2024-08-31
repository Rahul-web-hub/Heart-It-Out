<template>
  <div class="card mt-4">
    <div class="text-center header p-4">SECTION III [25 points]</div>
    <div class="card-body">
      <div class="position-relative">
        <button
          class="btn arrow-button position-absolute top-50 start-0 translate-middle-y"
          @click="prevTestimonial"
        >
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-chevron-left" viewBox="0 0 16 16">
  <path fill-rule="evenodd" d="M11.354 1.646a.5.5 0 0 1 0 .708L5.707 8l5.647 5.646a.5.5 0 0 1-.708.708l-6-6a.5.5 0 0 1 0-.708l6-6a.5.5 0 0 1 .708 0"/>
</svg>
        </button>
        <div class="text-center px-5 main-body">
          <blockquote class="blockquote position-relative">
            <img
              src="../assets/Group.svg"
              class="quote-open position-absolute"
              alt="Opening Quote"
            />
            <p>{{ testimonials[currentTestimonial].content }}</p>
            <img
              src="../assets/closing.svg"
              class="quote-close position-absolute"
              alt="Closing Quote"
            />
          </blockquote>
          <p class="text-muted">- {{ testimonials[currentTestimonial].author }}</p>
        </div>
        <button
          class="btn arrow-button position-absolute top-50 end-0 translate-middle-y"
          @click="nextTestimonial"
        >
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-chevron-right" viewBox="0 0 16 16">
  <path fill-rule="evenodd" d="M4.646 1.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1 0 .708l-6 6a.5.5 0 0 1-.708-.708L10.293 8 4.646 2.354a.5.5 0 0 1 0-.708"/>
</svg>
        </button>
      </div>
      <div class="text-center mt-3">
        <span
          v-for="(_, index) in testimonials"
          :key="index"
          class="dot"
          :class="{ active: index === currentTestimonial }"
          @click="setCurrentTestimonial(index)"
        ></span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentTestimonial: 0,
      testimonials: [
        {
          id: 1,
          content:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
          author: "Lorem Ipsum",
        },
        {
          id: 2,
          content: "Rahul",
          author: "Lorem Ipsum",
        },
      ],
    };
  },
  methods: {
    nextTestimonial() {
      this.currentTestimonial =
        (this.currentTestimonial + 1) % this.testimonials.length;
    },
    prevTestimonial() {
      this.currentTestimonial =
        (this.currentTestimonial - 1 + this.testimonials.length) %
        this.testimonials.length;
    },
    setCurrentTestimonial(index) {
      this.currentTestimonial = index;
    },
  },
};
</script>

<style scoped>
.dot {
  height: 10px;
  width: 10px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  margin: 0 5px;
  cursor: pointer;
}

.dot.active {
  background-color: #717171;
}

.card.mt-4 {
  color: #01818c;
  border: none;
  background-color: #ebf7fc;
}

.header {
  color: #01818c;
  font-size: 1.6rem;
}

.main-body {
  background-color: #ffff;
  height: 500px;
  width: 500px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: auto;
}

.arrow-button {
  background-color: #01818c;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  border: none;
  color: white;
  font-size: 1.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
}
.arrow-button i {
  font-size: 24px; 
  color: white; 
}
.arrow-button:hover {
  background-color: #015c6f;
  color: white;
}

.blockquote {
  position: relative;
  padding: 20px;
  font-size: 1.25rem;
  line-height: 1.5;
  margin: 0;
}

.quote-open {
  top: -20px;
  left: -20px; 
  width: 40px;
  height: 40px;
}

.quote-close {
  bottom: 5px; 
  right: -20px; 
  width: 40px;
  height: 40px;
}

@media (max-width: 768px) {
  .main-body {
    width: 100%;
    height: auto;
    margin-top: 2rem;
  }

  .quote-open, .quote-close {
    width: 30px;
    height: 30px;
  }
}
</style>
