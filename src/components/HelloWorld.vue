<template>
  <div class="surveyjs-root-container">
    <survey :survey="survey" />
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import * as Survey from "survey-vue";
import "survey-vue/modern.css";

@Component
export default class HelloWorld extends Vue {
  @Prop() private survey!: Record<string, unknown>;
  constructor() {
    super();
    Survey.StylesManager.applyTheme("modern");
    const json = {
      questions: [
        {
          type: "radiogroup",
          name: "car",
          title: "What car are you driving?",
          isRequired: true,
          colCount: 4,
          choices: [
            "None",
            "Ford",
            "Vauxhall",
            "Volkswagen",
            "Nissan",
            "Audi",
            "Mercedes-Benz",
            "BMW",
            "Peugeot",
            "Toyota",
            "Citroen",
          ],
        },
      ],
    };

    this.survey = new Survey.Model(json);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.surveyjs-root-container {
  text-align: left;
}
</style>
