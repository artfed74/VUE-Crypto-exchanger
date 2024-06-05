<template>
    <input @input="ChangeAmount($event.target.value)" placeholder="Введите число" min="0" type="number"><br>
    <button @click="convert()">Конвертировать</button>
    
  </template>
  
  <script>
  export default {
    props:{
        ChangeAmount:{
            type:Function,
            required:true
        },
        convert:{
            type:Function,
            required:true
        }
    }
  }
  </script>