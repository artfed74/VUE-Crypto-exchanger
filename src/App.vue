<template>
  <h1>Crypto exchanger</h1>
  <Input :ChangeAmount="ChangeAmount" :convert="convert"/>
<p>{{ error }}</p>
<p class="p">{{ result }}</p>
  <div className="selectors">
    <Select :setCrypto="setFirstvalue"/>
    <Select :setCrypto="setSecvalue"/>
  </div>

 
</template>

<script>
import Input from '@/components/input.vue';
import Select from '@/components/Select.vue';
import CryptoConvert from 'crypto-convert';

const convert = new CryptoConvert();
export default {
  components: {
    Input,
    Select
  },
  data(){
  return{
    amount:0,
    firstinput:'',
    secinput:'',
    error:'',
    result:''
  }
},
methods:{
  ChangeAmount(val){
    this.amount=val;
  },
  setFirstvalue(val){
    this.firstinput=val;
  },
  setSecvalue(val){
    this.secinput=val;
  },
  async convert(){
    if(this.amount<=0){
      this.error='Введите число больше 0';
      return;
    }
    else if(this.firstinput== '' || this.secinput==''){
      this.error='Выберите две валюты ';
      return;
    }
    else if(this.firstinput==this.secinput){
      this.error='Нельзя конвертировать одинаковые валюты';
      return;
    }
    this.error='';
    await convert.ready();
    if(this.firstinput =='Bitcoin' && this.secinput=='LTC'){
      this.result='Convert: '+convert.BTC.LTC(this.amount);
    }
    if(this.firstinput =='Bitcoin' && this.secinput=='USDT'){
      this.result='Convert: '+convert.BTC.USDT(this.amount);
    }
    if(this.firstinput =='LTC' && this.secinput=='Bitcoin'){
      this.result='Convert: '+convert.LTC.BTC(this.amount);
    }
    if(this.firstinput =='LTC' && this.secinput=='USDT'){
      this.result='Convert: '+convert.LTC.USDT(this.amount);
    }
    if(this.firstinput =='USDT' && this.secinput=='Bitcoin'){
      this.result='Convert: '+convert.USDT.BTC(this.amount);
    }
    if(this.firstinput =='USDT' && this.secinput=='LTC'){
      this.result='Convert: '+convert.USDT.LTC(this.amount);
    }
    
    
  }

}
}
</script>