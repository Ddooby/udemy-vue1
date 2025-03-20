<!-- Composition API -->
<script setup>
  import { ref, onMounted, watch } from 'vue';
  import ChildComp from './components/ChildComp.vue';

  let count = ref(0);
  let title = "Hello Vue";
  let color = ref("Green");

  onMounted(() => {
    console.log('On Mounted');
  })

  const increasedCount = () => {
    // count 변수가 ref 함수 안에 있는 값이기에 count 가 아니라 count.value 로 써줘야한다.
    // count++;
    count.value++;
  }

  // color 값이 변경될 때 callback 함수가 실행된다.
  watch(color, () => {
    console.log('color 변경');
  })
</script>

<template>
  <div>
    <h1>{{ title }}</h1>
    <button @click="increasedCount">Count++</button>
    <p>{{ count }}</p>
    <ChildComp :color="color" bgColor="yellow" />
    <button @click="color='red'">Change Color</button>
  </div>
</template>

<!-- scoped : 해당하는 컴포넌트에서만 사용하는 지역 스타일이라는 뜻 -->
<style scoped>
</style>
