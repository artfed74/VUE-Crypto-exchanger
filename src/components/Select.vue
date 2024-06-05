<template>
   <ul>
    <li @click="selectItem('Bitcoin')" :class="{ 'active': current === 'Bitcoin' }">Bitcoin</li>
    <li @click="selectItem('LTC')" :class="{ 'active': current === 'LTC' }">LTC</li>
    <li @click="selectItem('USDT')" :class="{ 'active': current === 'USDT' }">USDT</li>
   </ul>
    
  </template>
  
  <script>
  export default {
    props:{
        setCrypto:{
            type:Function,
            required:true
        }
    },
    data(){
        return{
            current:''
        }
    },
    methods:{
        selectItem(val){
            this.setCrypto(val);
            this.current=val;
        }
    }
    
  }
  </script>