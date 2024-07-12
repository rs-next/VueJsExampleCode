<template>
  <div class="container">
      <div class="container-navigation">
          <!-- @click 사용 -->
          <button @click="addNum">+</button>          
          <!-- @click 사용 -->
          <button @click="removeNum">-</button>          
      </div>
      <div class="container-description">
          <p>아이템을 추가해보세요</p>
          <p>현재 {{num}} 개</p>
          <!-- v-if 사용 -->
           
          <p class="warning" v-if="(num >= 10)" >아이템이 너무 많아요!</p>
      </div>
      <ul class="container-list">
          <!-- v-for 사용 -->
          <li v-for="(item, index) in itemsNum" :key="index"> {{ item.numIndex }} </li>
      </ul>
  </div>
</template>

<script setup>
  import {ref} from 'vue';

  const num = ref(0);
  const itemsNum = ref([
	
])
function addNum(){
  num.value += 1;
	itemsNum.value.push({numIndex : num.value});
	
}

function removeNum(){
	if(itemsNum.value.length != 0){
    num.value -= 1;
		itemsNum.value.pop({numIndex : num.value});
		
	}
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  row-gap: 30px;
  align-items: center;
  padding: 30px;

  .container-navigation {
      display: flex;
      column-gap: 10px;

      > button {
          font-size: 22px;
          font-weight: bold;
          width: 40px;
          height: 40px;
          border-radius: 8px;
          cursor: pointer;
      }
  }

  .container-description {
      > p {
          text-align: center;
          font-size: 16px;

          &.warning {
              margin-top: 1rem;
              font-size: 12px;
              color: orange;
          }
      }
  }

  .container-list {
      list-style: none;
      display: flex;
      gap: 10px;
      flex-wrap: wrap;

      > li {
          font-size: 16px;
          border: 1px solid #000;
          width: 40px;
          line-height: 40px;
          text-align: center;
      }
  }
}
</style>