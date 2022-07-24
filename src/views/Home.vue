<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/> -->


<div class="header bg-blend-hard-light text-5xl h-20 shadow-md" >
  <h2>Replaceator</h2>
</div>

<div class="row">
  <div class="column bg-blue-300">
    <div class="row">
      Place input values as csv:
    </div>
  <div class="row">'$0;$1;$2' etc..</div>
    <div class="row">
      <textarea type="text" style="width: 100%; margin-top: 0px; margin-bottom: 0px; height: 205px;" v-model="myData.inputvalue"/>
    </div>
  </div>

  <div class="column bg-green-400">
    <div class="row">
      Place template text with arguments specified as 
    </div>
    <div class="row">$0 as first element, $1 as second element etc..</div>
    <div class="row">
      <textarea type="text" style="width: 100%; margin-top: 0px; margin-bottom: 0px; height: 205px;" v-model="myData.inputTemplate"/>
    </div>
    <div class="row mt-6">
      <button type="button" class="rounded-full bg-indigo-200 hover:bg-indigo-100 border-gray-900 border-2 pl-2 pr-2 pt-2 pb-2" v-on:click="computeValues()">replace</button>
    </div>
  </div>

  <div class="column bg-blue-200">

<div class="row">
Result below:
</div>

<div class="row mt-6">
<input id="resultTemplate" type="text" class="bg-pink-50" style="width: 100%; margin-top: 0px; margin-bottom: 0px; height: 205px;" v-model="myData.resultTemplate" disabled="true" />
</div>

 <div class="row mt-6">
      <button type="button" class="rounded-full bg-indigo-200 hover:bg-indigo-100 border-gray-900 border-2 pl-2 pr-2 pt-2 pb-2" v-on:click="copyToClipboard()">copy to clipboard</button>
    </div>
  </div>
</div>

<div class="footer">
  <p>Alexandre boungnarith</p>
</div>


  </div>
</template>

<script lang="ts">
import { Component,  Vue } from 'vue-property-decorator';
// import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

@Component({
  components: {
    
  },
})
export default class Home extends Vue {

myData: {inputvalue: string;
        inputTemplate: string;
        resultTemplate: string;
        } = {inputvalue : 'test1;test2;test3\ntest4;test5;test6', 
        inputTemplate : 'first item is $0, second item is $1, last item is $2', 
        resultTemplate:''}


computeValues(){
  const valuescsv = this.myData.inputvalue;
  const templateValuescsv = this.myData.inputTemplate;

  if(valuescsv){
    
      let comptutedtemplateWithArg = '';
        valuescsv.split('\n').forEach(line => {
        let templateComputed = templateValuescsv;
        const splittedVals = line.split(';');
        
        splittedVals.forEach( (val, index) => {
          templateComputed = templateComputed.replace('$'+index, val);
        })
        comptutedtemplateWithArg += templateComputed+'\n';
      })
    this.myData.resultTemplate=comptutedtemplateWithArg;
  }
}

copyToClipboard(){    
  if(this.myData.resultTemplate){
    navigator.clipboard.writeText(this.myData.resultTemplate);
  }

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
