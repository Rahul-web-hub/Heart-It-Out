<template>
  <div class="card mb-4">
    <div class="header d-flex justify-content-center">SECTION I [15 points]</div>
    <div class="card-body mt-4">
      <form @submit.prevent="submitForm" class="d-flex flex-column align-items-center">
        <div class="content-wrapper">
          <div class="mini-sections mb-3 d-flex flex-column">
            <label class="form-label">Lorem ipsum dolor sit amet</label>
            <div class="mb-2" v-for="(option, index) in radioOptions" :key="'radio'+index">
              <input type="radio" :id="'radio'+index" v-model="selectedRadio" :value="option" class="me-2">
              <label :for="'radio'+index">{{ option }}</label>
            </div>
          </div>
          
          <div class="mb-3 mt-5">
            <label class="form-label">Lorem ipsum dolor sit amet</label>
            <select v-model="selectedDropdown" class="form-select">
              <option v-for="option in dropdownOptions" :key="option" :value="option">{{ option }}</option>
            </select>
          </div>
          
          <div class="mb-3 mt-5">
            <label class="form-label">Lorem ipsum dolor sit amet</label>
            <div class="mb-2" v-for="(option, index) in checkboxOptions" :key="'checkbox'+index">
              <input type="checkbox" :id="'checkbox'+index" v-model="selectedCheckboxes" :value="option" class="me-2">
              <label :for="'checkbox'+index">{{ option }}</label>
            </div>
          </div>
        </div>
        
        <div class="w-100 d-flex justify-content-center mt-4">
          <button type="submit" class="btn custom-button">SUBMIT</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      radioOptions: ['Radio Button Option 1', 'Radio Button Option 2', 'Radio Button Option 3'],
      selectedRadio: '',
      dropdownOptions: ['Drop Down Option 1', 'Drop Down Option 2', 'Drop Down Option 3'],
      selectedDropdown: '',
      checkboxOptions: ['Checkbox Option 1', 'Checkbox Option 2', 'Checkbox Option 3'],
      selectedCheckboxes: []
    }
  },
  methods: {
    submitForm() {
      console.log('Form submitted', {
        radio: this.selectedRadio,
        dropdown: this.selectedDropdown,
        checkboxes: this.selectedCheckboxes
      })
    }
  }
}
</script>

<style scoped>
button{
  background-color: #01818C;
  color: white;
}
.btn:hover {
  background-color:#01818C; 
  color: white; 
}
.card{
  
  border: none;
}
.mb-3{
  font-size:1.2rem ;
}
.header{
    color: #01818C;
    font-size: 1.6rem;
}
.content-wrapper {
  width: 100%;
  max-width: 1000px;
  padding-right: 5rem;
}

@media (max-width: 768px) {
  .content-wrapper {
    padding-left: 0;
  }
}
</style>