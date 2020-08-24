<template>
  <div class="container">
    <h1>SignUp</h1>
    <div class="form-container">
      <label for="ID"><b>ID</b></label>
      <div class="ID">
        <input type="text" v-model="userInfo" id="id" placeholder="Enter ID" name="ID" class="blink-2" required>
      </div>
      <label for="psw"><b>Password</b></label>
      <div class="PSW">
        <input type="password" placeholder="Enter Password" name="psw" id="pwd" v-model="password" class="blink-2" required>
      </div>

      <label for="psw2"><b>Password2</b></label>
      <div class="PSW2">
        <input type="password" placeholder="Password2" name="password2" id="pwd2" v-model="password2" class="blink-2" required>
      </div>
      <label for="Major"><b>Major</b></label>
      <div class="Major">
        <select id="country" name="country">
          <option value="0">None</option>
          <option value="1">인뭄과학대학</option>
          <option value="2">사회과학대학</option>
          <option value="3">경영경제대학</option>
          <option value="4">호텔관광대학</option>
          <option value="5">자연과학대학</option>
          <option value="6">생명과학대학</option>
          <option value="7">전자정보공학대학</option>
          <option value="8">소프트웨어융합대학</option>
          <option value="9">공과대학</option>
          <option value="10">예체능대학</option>
          <option value="11">법학부</option>
        </select>
      </div>
      <div class="logo">
      </div>
      <button type="button" class="jello-horizontal">Submit</button>
    </div>
  </div>
</template>
<script>
  export default {
      name: "SignUpComponent",
      data(){
        return{
            userInfo:'',
            onlyNumber:'',

            password: '',
            password2:'',
        }
      },
      watch:{
        /*
      userInfo(val){
            const reg = /[ㄱ-ㅎ|ㅏ-ㅣ|가-힣]/;

          if(reg.exec(val)!==null){
          return this.userInfo = this.userInfo.slice(0,-1);
          }
      },*/
      'userInfo':'isValidateID',
      'password':'isValidatePW',
      'password2':'isValidatePW2'

    },
    methods: {
      isValidatePW(){

        const passRule= /^[A-Za-z0-9]{6,12}$/;
        if(!passRule.test(document.getElementById('pwd').value)) {
            console.log('fail');
        }
        else{console.log('success');}
      },
      isValidatePW2(){

        if(document.getElementById('pwd').value!=document.getElementById('pwd2').value){
          console.log('incorrect');
        }
        else{console.log('correct');}
      },
      isValidateID(){
        const reg = /[ㄱ-ㅎ|ㅏ-ㅣ|가-힣]/;
        if(reg.test(document.getElementById('id').value)) {
            console.log('fail');
        }
        else{console.log('success');}
      }
    }
  }

</script>

<style lang="scss" scoped>
    @import './SignUpComponent.scss';
</style>
