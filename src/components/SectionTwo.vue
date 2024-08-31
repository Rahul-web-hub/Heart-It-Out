<template>
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-md-10"> <!-- Increased column width for more space -->
        <div class="card mb-4">
          <div class="header text-center">SECTION II [20 points]</div>
          <div class="card-body">
            <div class="accordion" id="mainAccordion">
              <div v-for="(item, index) in randomWordsWithShows" :key="index" class="accordion-item mt-3">
                <h2 class="accordion-header">
                  <button
                    class="accordion-button centered-text"
                    type="button"
                    :data-bs-toggle="'collapse'"
                    :data-bs-target="'#collapse' + index"
                    aria-expanded="true"
                    :aria-controls="'collapse' + index"
                  >
                    {{ item.word }}
                  </button>
                </h2>
                <div
                  :id="'collapse' + index"
                  class="accordion-collapse collapse"
                  data-bs-parent="#mainAccordion"
                >
                  <div class="accordion-body text-align-center">
                    <div class="row">
                      <div
                        v-for="(show, i) in item.shows"
                        :key="i"
                        class="col-md-4 mb-3"
                      >
                        <div class="card h-100">
                          <div class="card-body d-flex flex-column align-items-center text-center">
                            <h5 class="card-title">{{ show.show.name }}</h5>
                            <p class="card-text" v-html="show.show.summary"></p>
                            <p class="card-text mt-auto">
                              <strong>Rating: {{ show.show.rating?.average || 'N/A' }}</strong>
                            </p>
                            <a :href="show.show.url" target="_blank" class="btn btn-primary mt-2">View Show</a>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      randomWords: ["apple", "house", "dream", "star"],
      randomWordsWithShows: []
    };
  },
  mounted() {
    this.fetchShowsForWords();
  },
  methods: {
    async fetchShowsForWords() {
      for (const word of this.randomWords) {
        try {
          const response = await fetch(`https://api.tvmaze.com/search/shows?q=${word}`);
          const data = await response.json();
          this.randomWordsWithShows.push({
            word: word,
            shows: data.slice(0, 3)
          });
        } catch (error) {
          console.error(`Error fetching shows for ${word}:`, error);
        }
      }
    }
  }
};
</script>

<style scoped>
.container {
  margin-top: 4rem;
}

.card.mb-4 {
  border: none;
}

.accordion-button {
  background-color: #01818C;
  color: white;
  position: relative;
  text-align: center;
  padding-left: 40px;
  padding-right: 40px;
}

.accordion-button:not(.collapsed) {
  background-color: #01818C;
  color: white;
}

.accordion-button::after {
  position: absolute;
  right: 20px;
}

.centered-text {
  display: flex;
  justify-content: center;
}

.accordion-body {
  padding: 1.5rem; 
}

.header {
  color: #01818C;
  font-size: 1.6rem;
}

.btn-primary {
  background-color: #01818C;
  border-color: #01818C;
}

.btn-primary:hover {
  background-color: #015c63;
  border-color: #015c63;
}

@media (max-width: 768px) {
  .col-md-10 {
    width: 100%;
    padding-left: 0;
    padding-right: 0;
  }

  .accordion-body {
    padding: 1rem; 
  }
}
</style>