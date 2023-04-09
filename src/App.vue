<template>
  <div class="container">
 <h1>What is for dinner?</h1>
 <button v-if="!randomDinner" @click="getRandomDinner">Get dinner</button>
 
 <div v-if="randomDinner">
 <h1>{{ randomDinner.name }}!</h1>
<img width="400" :src="randomDinner.image">
<h3>Main ingredients:</h3>
<ul v-for="ingredients in randomDinner.ingredients" :key="ingredients">
  <li> {{ ingredients }}</li>
</ul>
  </div>
  <div v-else>
<h3>No dinners yet! Click the button to get one</h3>
  </div>
  <button v-if="randomDinner" @click="getRandomDinner">Get another dinner</button>
  </div>

 </template>
 
 <script>
 import dinnerData from './assets/data/dinners.json';
 
 export default {
   data() {
     return {
       dinners: [],
       randomDinner: ''
     };
   },
   mounted() {
     this.dinners = dinnerData;
   },
methods: {
getRandomDinner() {
const randomIndex = Math.floor(Math.random() * this.dinners.length);
this.randomDinner = this.dinners[randomIndex]
console.log('Function works')
}
}
 };
 </script>
 
 <style>
 .container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 5em;
 }

 h1 {
  text-align: center;
  font-family: 'Roboto', sans-serif;
 }

 h3 {
  font-family: 'Roboto', sans-serif;
 }

 li {
  list-style-type: none;
  font-family: 'Roboto', sans-serif;

 }

 ul {
  padding: 0px;
 }

 button {
background-color: green;
color: white;
border: none;
padding: 10px;
font-weight: bold;
 }

 button:hover{
  background-color: darkgreen;
 }
 </style>