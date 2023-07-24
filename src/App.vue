<script setup>
  import { ref } from 'vue'
  import { computed } from 'vue'
  import BtnTypeA from './components/ButtonTypeA.vue'

  function function1() {
    console.log( randomNumber.value, ': function1')
    randomNumber.value = Math.floor(Math.random() * 10)
  }
  function function2() {
    console.log(randomNumber.value, ': function2')
    randomNumber.value = Math.floor(Math.random() * 10)
  }
  const randomNumber = ref(
    Math.floor(Math.random() * 10)
  )
  const isEven = computed(()=> {
    if(randomNumber.value % 2 === 0) return true
    else return false
  })
  const isNumber = computed(()=> {
    if(isNaN(randomNumber.value)) return false
    else return true
  })
</script>

<template>
  <div class="flex flex-col justify-center items-center gap-12">
    <ul class="list-disc list-inside"> 
      <li class="font-semibold list-none">Objective :</li>
      <li>to shape the button dynamically, depending on the whether the input is and Even or Odd number</li>
      <li>to disable the button if input is not a number</li>
      <li>to pass different function base on the input</li>
      <li>to maintain modularity and reusability of created component</li>

      <li>
        <a href="https://github.com/zulfidly/single-button" target="_blank" aria-label="visit Github repository">Github link</a>
      </li>
      <li>
        <a href="https://verdant-figolla-f43a03.netlify.app/" target="_blank" aria-label="view app demo at Netlify">Demo at Netlify</a>
      </li>
    </ul>
    
    <BtnTypeA
      :btn-name="randomNumber.toString()"
      :btn-aria-label="'custom button'"
      :btn-function="isEven ? function1 : function2"
      :disabled="isNaN(randomNumber)"
      :btn-class="['transition-all duration-300',
        isNumber ? [isEven ? 'px-28 py-2 bg-red-300 rounded-lg' : 'px-28 py-2 bg-red-200 rounded-xl'] : 'px-28 py-2 bg-slate-300' ]"
    />
  
    <section>
      Preview button label :
      <input class="flex border" v-model="randomNumber" />
      <span>{{ isNumber ? isEven ? 'Even number' : 'Odd number' : 'not a number' }}</span>
    </section>

  </div>


</template>


