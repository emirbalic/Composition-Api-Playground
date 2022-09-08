<template>
  <div class="home">
    <h2>{{appTitle}}</h2>
    <h3>{{counterData.title}}:</h3>
    <div>
      <button @click="decreaseCounter(2)" class="btn">-2</button>
      <button @click="decreaseCounter(1)" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter(1)" class="btn">+1</button>
      <button @click="increaseCounter(2)" class="btn">+2</button>
    </div>

    <p>This counter is {{oddOrEven}}</p>

    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterData.title" type="text">
    </div>
  </div>
</template>


<script setup>
import { reactive, computed, watch } from "vue";//, ref

// const counter = ref(0),
// counterTitle = ref('My Counter');

const appTitle = 'Cool title app'

const counterData = reactive({
  count: 0,
  title: 'Reactive Counter'
});

watch(()=> counterData.count, (newCount, oldCount) =>{
  if(newCount === 20) {
    alert('It was ' + oldCount +' and now it is ' + newCount);
  }
})

const oddOrEven = computed(() => {
  if(counterData.count % 2 === 0) return 'even';
  return 'odd'
})

const increaseCounter = amount => {
  // counter.value++;
  // counterData.count++
  counterData.count += amount
};
const decreaseCounter = amount => {
  // counter.value--;
  // counterData.count--
  counterData.count -= amount
};
</script>



<style scoped>
.home {
  text-align: center;
  padding: 20px;
}
.btn,
.counter {
  font-size: 40px;
  margin: 20px;
}
.edit {
  margin-top: 60px;
}
</style>



<!--
<script>
import { ref } from "vue";
export default {
  setup() {
    const counter = ref(0);

    const increaseCounter = () => {
      counter.value ++
    }
    const decreaseCounter = () => {
      counter.value --
    }

    return {
      counter,
      increaseCounter,
      decreaseCounter
    };
  },
};
</script>
-->


<!--<script>
export default {
  data() {
    return {
      counter: 0
    }
  },
  methods: {
    increaseCounter() {
      this.counter ++;
    },
    decreaseCounter() {
      this.counter --;
    }
  }
}
</script>

-->
 