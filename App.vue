<template>
  
<input type="text" v-bind:value="abbr">
<input type="text" v-model="normal">
<hr>
<div>{{normal}}</div>
<div>{{abbr}}</div>
<p v-if="normal==='N'">normal is N</p>
<hr>
<div>counter: {{counter}}</div>
<div>counter2: {{counter2}}</div>

<p v-if="counter < 5">counter less 5</p>
<p v-else-if="counter === 5">counter is 5</p>
<p v-else>counter bigger 5</p>

<button v-on:click="counter++">add</button>
<button v-on:click="onClick2">add2</button>

<div>
  <ol>
    <li v-for="elem in items">
      <input type="text" v-bind:value="elem">
    </li>
  </ol>
</div>

<div>
  <ol>
    <li v-for="(elem, key, idx) in objItem">
     idx: {{idx}},key:{{key}},elem:{{elem}}
    </li>
  </ol>
</div>

<input type="text" v-model="result.name">
<input type="radio" name="gender" v-model="result.gender" value="male">M
<input type="radio" name="gender" v-model="result.gender" value="female">W
<div>
  <span v-for="hobby in hobbys" >
    <input type="checkbox" v-model="result.hobby" v-bind:value="hobby">
    <label>{{hobby}}</label>
  </span>
</div>

<div>
  <select v-model="result.country">
    <option v-for="(element, index) in countrys">
    {{index}}.{{element}}
    </option>
  </select>
</div>

<hr>
{{result}}

</template>

<script >
import {reactive, ref} from 'vue'

export default {
  data() {
    return {
      counter2 : 0
    }
  },
  setup(){
    const abbr = ref('sample')
    const normal = ref('')
    let counter = ref(0)
    const name ='';
    const gender='';
    const hobby=[];
    const hobbys = ['sports','photo','music','movie']
    const country ='';
    const countrys = ['kr','us','cn','jp']
    
    const items = reactive(['first','second','third','fourth'])
    const objItem = {"one":'first', "two":'second', "three":'third', "four":'fourth' }

    const result = reactive( {name, gender,hobby,country} )

    return { abbr,normal, counter, items , objItem , result, hobbys, countrys}
  },
  methods: {
    onClick2: function (evt){
      if(evt){  evt.preventDefault() }
      this.counter2++
    }
  }
}

</script>
