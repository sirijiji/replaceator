<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/> -->


<div class="header">
  <h2>Replaceator</h2>
</div>

<div class="row">
  <div class="column bg-blue-300">
    <div class="row">
      Place input values as csv:
    </div>
    <div class="row">
      <textarea type="text" style="width: 100%" v-model="myData.inputvalue"/>
    </div>
  </div>

  <div class="column bg-green-400">
    <div class="row">
      Place template text with arguments specified as 
    </div>
    <div class="row">
      <textarea type="text" style="width: 100%" v-model="myData.inputTemplate"/>
    </div>
    <div class="row mt-4">
      <button type="button" class="bg-gray-200" v-on:click="computeValues()">transform</button>
    </div>
  </div>

  <div class="column bg-purple-400">

<div class="row">
Result below:
</div>

<div class="row pt-4">
  <p class="text-lg" >
<input type="text" class="bg-pink-50" v-model="myData.resultTemplate" disabled="true" />

  </p>
</div>

  </div>
</div>

<div class="footer">
  <p>Footer</p>
</div>


  </div>
</template>

<script lang="ts">
import { Component,  Vue } from 'vue-property-decorator';
// import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

@Component({
  components: {
    // HelloWorld,
  },
})
export default class Home extends Vue {

myData: {inputvalue: string;
        inputTemplate: string;
        resultTemplate: string;
        } = {inputvalue : 'values', 
        inputTemplate : 'template', 
        resultTemplate:''}


computeValues(){
  const valuescsv = this.myData.inputvalue;
  const templateValuescsv = this.myData.inputTemplate;

  console.log(valuescsv);
  console.log(templateValuescsv);

  this.myData.resultTemplate=valuescsv + templateValuescsv;

}




}
</script>
<style>
* {
  box-sizing: border-box;
}

body {
  font-family: Arial, Helvetica, sans-serif;
}

/* Style the header */
.header {
  background-color: #f1f1f1;
  padding: 10px;
  text-align: center;
  font-size: 10px;
}

/* Container for flexboxes */
.row {
  display: -webkit-flex;
  display: flex;
}

/* Create three equal columns that sits next to each other */
.column {
  -webkit-flex: 1;
  -ms-flex: 1;
  flex: 1;
  padding: 10px;
  height: 500px;
  /* height: 300px; Should be removed. Only for demonstration */
}

/* Style the footer */
.footer {
  background-color: #f1f1f1;
  padding: 10px;
  text-align: center;
}

/* Responsive layout - makes the three columns stack on top of each other instead of next to each other */
@media (max-width: 600px) {
  .row {
    -webkit-flex-direction: column;
    flex-direction: column;
  }
}
</style>
