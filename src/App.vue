<template>
<learning-survey ></learning-survey>
<user-experiences ></user-experiences>
</template>

<script>

import LearningSurvey from "@/components/survey/LearningSurvey";
import UserExperiences from "@/components/survey/UserExperiences";
export default {
  name: 'App',
  components: {
    UserExperiences,
    LearningSurvey
  },
  // data() {
  //   return {
  //     savedSurveyResults: []
  //   }
  // },
  // methods: {
  //   storeSurvey(surveyData) {
  //     const surveyResult = {
  //       name: surveyData.userName,
  //       rating: surveyData.rating,
  //       id: new Date().toISOString()
  //     };
  //     this.savedSurveyResults.push(surveyResult);
  //     console.log(surveyResult)
  //   }
  // }

}
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>
