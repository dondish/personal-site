<template>
  <div id="achievements" class="pt-20 md:pt-8 text-center">
    <h1 class="text-4xl font-bold">Achievements</h1>
    <div class="text-left mx-8 mb-8" v-for="achievement of achievements" :key="achievement.title">
        <h2 class="texl-l md:text-xl font-bold">{{achievement.title}}</h2>
        <ul class="list-disc list-inside">
          <li class="font-light" v-for="item of achievement.listItems" :key="item">{{item}}</li>
        </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Achivements',
  data () {
    return {
      achievements: [
        {
          title: 'Israeli IOI Team Member – 2018, 2020',
          listItems: ['2018: Ranked 20th in Israel. Excellence.', '2020: Ranked 10th in Israel. 6th place in the Internal Olympiad.']
        },
        {
          title: 'Certifications',
          listItems: ['Machine Learning – Stanford University - Coursera', 'Neural Networks and Deep Learning – Deeplearning.ai - Coursera', 'Improving Deep Neural Networks: Hyperparameter tuning, Regularization and Optimization - Deeplearning.ai - Coursera', 'Structuring Machine Learning Projects - Deeplearning.ai - Coursera', 'Convolutional Neural Networks - Deeplearning.ai - Coursera']
        },
        {
          title: 'Competitions',
          listItems: ['Reply Code Challenge – Teen – 53rd place – March 12th, 2020', 'Google Hashcode – 630th place – February 20th, 2020', 'Skillz Programming – High School Internal Competition – 1st place – 2018 to 2020']
        }
      ]
    }
  }
}
</script>
