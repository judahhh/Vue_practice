<template>
<!-- 반복문 안쓰고 카드 하나만 컴포넌트화 해서하는게 재사용이 더 잘될거같은  -->
   <div>
  <img :src="원룸들.image" alt="" class="room-img">
  <!-- ./는 현재경로라는 뜻->src폴더 안에 있는거 가져올때 경로는 ./부터 -->
  <!-- 자식에서 부모 데이터 수정하는 방법-> -->
  <h4 @click ="$emit('openModal',원룸들.id)">{{원룸들.title}}</h4>
  <p>{{원룸들.price}}원</p>
  </div>
</template>

<script>
export default {
name:'Card',
props:{
원룸들:Object,
}
}
</script>

<style>

</style>