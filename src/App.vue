<template>
  <div>
    <input v-model="text" placeholder="Type Here" :style="inputStyle">
    <p>{{ text }}</p>
    <button @click="CekPalindrome">Cek Palindrome</button>
    <p v-if="isPalindrome" :class="{ 'palindrome': isPalindrome, 'not-palindrome': !isPalindrome }">Kata ini Palindrome</p>
    <p v-else :class="{ 'palindrome': isPalindrome, 'not-palindrome': !isPalindrome }">Kata ini Bukan Palindrome</p>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const text = ref('')
const reversingText = ref('')
const isPalindrome = ref(true)

function CekPalindrome() {
  reversingText.value = text.value.split("").reverse().join("").toLowerCase();
  isPalindrome.value = text.value.toLowerCase() === reversingText.value;
}

const inputStyle = computed(() => ({
  border: isPalindrome.value ? '2px solid green' : '2px solid red',
}))
</script>

<style scoped>
.palindrome {
  color: green;
}

.not-palindrome {
  color: red;
}
</style>
