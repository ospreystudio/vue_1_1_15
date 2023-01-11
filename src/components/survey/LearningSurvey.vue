<template>
<base-card>
  <h2>How was you learning experience?</h2>
  <form @submit.prevent="submitSurvey">
    <div class="form-control">
      <label for="name">Your name</label>
      <input type="text" id="name" name="name" v-model.trim="enteredName">
    </div>
    <h3>My learning experience was ...</h3>
    <div class="form-control">
      <input type="radio" id="rating-poor" value="poor" name="rating" v-model="chosenRating">
      <label for="rating-poor">Poor</label>
    </div>
    <div class="form-control">
      <input type="radio" id="rating-average" value="average" name="rating"  v-model="chosenRating">
      <label for="rating-average">Average</label>
    </div>
    <div class="form-control">
      <input type="radio" id="rating-great" value="great" name="rating"  v-model="chosenRating">
      <label for="rating-great">Great</label>
    </div>
    <p v-if="invalidInput">
      One or more inputs are invalid. Please check your provided data
    </p>
    <p v-if="error">{{ error }}</p>
    <base-button>Submit</base-button>
  </form>
</base-card>
</template>

<script>


export default {
  name: "LearningSurvey",
  data() {
    return {
      enteredName:'',
      chosenRating: null,
      invalidInput: false,
      error: null
    }
  },
  methods: {
    submitSurvey() {
      if (this.enteredName === '' || !this.chosenRating) {
        this.invalidInput = true
        return
      }
      this.invalidInput = false

      this.error = null
      fetch('https://vue-lessons-efa87-default-rtdb.firebaseio.com/survey.json', {
        method: 'POST',
        headers: {
          'Content-type' : 'application/json'
        },
        body:  {
          name: this.enteredName,
          rating: this.chosenRating
        }
      }).then(response => {
        if (response.ok) {
          // do something
        } else {
          throw new Error('Could not save data')
        }

      }).catch((error) => {
          // console.log(error)
        this.error = error.message
      })

      this.enteredName = '';
      this.chosenRating = null
    }
  }
}
</script>

<style scoped>
.form-control {
  margin: 0.5rem 0;
}

input[type='text'] {
  display: block;
  width: 20rem;
  margin-top: 0.5rem;
}
</style>