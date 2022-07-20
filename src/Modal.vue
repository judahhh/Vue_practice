<template>
  <!-- 모달창 -->
<div class ="black-bg" v-if="모달창==true">
  <!-- v-if ="조건식" -> 안에 있는 조건식이 참일 때만 html보여줌 -->
  <div class ="white-bg">
   <button v-on:click ="$emit('closeModal')">x</button> 
    <!-- Modal.vue가 App.vue에 있는 데이터 수정하고 싶으면
    즉, 자식이 부모 컴포넌트에 있는 데이터 수정하고 싶으면 custom event 사용 -->
    <h4>{{원룸들[clicknum].title}}</h4>
        <img :src="원룸들[clicknum].image" alt="">
    <p>{{원룸들[clicknum].content}}</p>

    <input v-model.number="month" type="text">
     <!-- <input @input="month=$event.target.value" type="text" name="" id=""> -->
    <p>{{month}}개월 선택함 : {{원룸들[clicknum].price*month}} 원</p>
    <!-- input안 value값을 문자로 인식함-> +기호 쓰면 사칙연산이 아니라 연결연산이 됨 -->
    <!-- 이를 숫자로 인식하게 하려면 v-model.number -->
   
    
  </div>
</div>
</template>

<script>
export default {
name:'Modal',
data(){
return{
  month:1,
  // 초깃값을 1로 해서 Number라고 인식, 문자로 입력받고 싶으면 
  //초깃값을 문자로 설정해놓을것
}
},
watch:{
  // month라는 데이터가 변할때마다 month()안에 있는 코드 실행됨
// value값을 파라미터로 받음, 함수명은 감시할 데이터 이름으로 작명할것
month(a,b){  //a는 변경될 데이터, b는 변경 전 month데이터
// 사용자가 month를 문자로 입력하면 경고문을 띄워주세요
if(isNaN(a)){
  alert("개월 수를 숫자로 입력하세요");
  this.month=1;
}
},
},
props:{
  원룸들:Object,
  clicknum:Number,
  모달창:Boolean,
  // 2. 자식은 부모에게 props로 받은거 등록
}
}
</script>

<style>

</style>