<template>
<!-- 상단 nav메뉴 -->
<div class="menu">
  <!-- vue의 html반복문 : <태그명 v-for="작명 in 몇회" :key="작명">  
  여기서 key=""는 반복문 쓸때 꼭 써야함, 반복문 돌린 요소를 컴퓨터가 구분하기 위해 씀-->
  <!-- but 우리는 같은 것을 반복하고 싶지 않음 : 3 자리에 데이터를 집어넣기
  반복문 횟수에 array, object집어넣기 가능
  ->그럼 자료 안의 데이터 갯수만큼 반복됨, 작명한 변수는 데이터안의 자료가 됨 -->
<a v-for="i in menu" :key="i">{{i}}</a>

</div>


<!-- 로고 image -->
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <img src="./assets/room0.jpg" alt="" class="room-img">
  <!-- ./는 현재경로라는 뜻->src폴더 안에 있는거 가져올때 경로는 ./부터 -->
  <div v-for="(a,i) in products" :key="a">
     <!--데이터바인딩 : js데이터를 html에 꽂아넣는 문법  -->
    <!-- 데이터보관함에 있는 데이터를 여기에 넣고 싶으면 {{데이터 이름}}-->
    <h4 :style="style">{{a}}</h4>
    <!-- 속성값 안에 데이터바인딩하려면 {{}} 말고 속성 앞에 :붙일 것-->
    <p>{{pricye1}}만원</p>
    <!-- 허위매물신고 버튼을 누르면 신고수가 1 증가되게 해보자 (이벤트핸들러이용)-->
    <!-- v-on:을 @로 축약할 수도 있음 -->
    <!-- 뷰로 개발하면 실시간 렌더링이 되기 때문에 신고수 데이터에 +1을 해주면 html에 바로 반영됨 -->
    <button v-on:click ="increase(i)">허위매물신고</button> <span>신고수 : {{신고수[i]}}</span>
    <!-- 따옴표 안에 자바스크립트코드가 길어지면 script태그에 함수를 만들어서 함수 사용 가능
     ->함수 이름만 첨부할 것 -->
    <!-- click말고도 @mouseover 등등 많음 -->

    
  </div>
  
  <!-- 데이터바인딩 하는 이유 
    1. html에 하드코딩해놓으면 나중에 변경이 어려움 ex)쇼핑몰 상품가격은 매번 변동됨
    2. vue가 제공하는 실시간 자동 렌더링 쓰기 위해서는 데이터바인딩 써야함
    (vue는 데이터를 변경하면 데이터와 관련된 html에도 실시간으로 반영,재렌더링됨
    ->웹앱을 만들 수 있음, 가격 필터 같은 경우 우리가 바꾸는 족족 부드럽게 전환됨  )
    ->자주 변할거같은 데이터들은 데이터로 보관하고 html에 꽂아넣는 방식으로 개발해야함
    Q&A. 쇼핑몰 로고같은 잘 바뀌지 않는 것들은 데이터바인딩 하지 않아도 됨-->
   
   <!-- html속성(class나 style같은 것들)도 데이터 바인딩 가능함 -->
</template>

<script>


export default {
  name: 'App',
  data(){ //vue의 js데이터 보관함->데이터는 object자료로 저장해야함
    return {
      price1:50,
      price2:70,
      pricenone:'가격은 아무거나',
      style:'font-weight:bold',
      menu:['Home','Products','About'],
      products:['역삼동원룸','천호동원룸','마포구원룸'],
      신고수:[0,0,0],
    }
  },
  components: {
    
  },

  // 뷰에서 함수 만들고 싶을 때 이 공간 안에 선언
  methods:{
    increase(i){
      // 함수 안에서 데이터 보관함 안의 데이터 쓸 때는 this.데이터명
      this.신고수[i]++;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu{
  background: sandybrown;
  padding: 15px;
  border-radius: 5px;

}
.menu a{
  color: white;
  padding:10px;
}
.room-img{
  width:100%;

  margin-top:40px;
}

</style>
