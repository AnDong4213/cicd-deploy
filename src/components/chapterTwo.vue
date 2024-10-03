<template>
  <div class="hello">
    HelloWorld
  </div>
</template>

<script setup>
import { onMounted } from 'vue';

const plog = console.log
{
  // 判断是不是Object
  // console.log(typeof null) // object，
  // 是一个历史遗留问题，追溯到js的第一个版本，在这个版本，所有的值都是用 32 位（或 64 位）的浮点数表示的（数值是以32字节(bit)存储的），由标志位（1~3个字节）和数值组成。标志位存储的是低位的数据。
  // 这是因为javascript中不同对象在底层都表示为二进制，而javascript 中会把二进制前三位都为0的判断为object类型，而null的二进制表示全都是0，自然前三位也是0，所以执行typeof时会返回'object。001：整型(int)，010：双精度浮点型(double)，110：布尔值
  // null是一种基本数据类型，存储在栈区；而typeof null的结果却是Object，而Object是引用数据类型，存储在堆区。
  // 现在的V8引擎不是这么判断的，为什么没有修复
  // 尽管这个问题在后来的 JavaScript 标准化过程中被广泛讨论，但修改 typeof null 的行为会带来大量的兼容性问题。许多现有的代码库依赖于 typeof null === "object" 这一事实。因此，为了保持向后兼容性，ECMAScript 标准决定保留这一行为。
}

{
  // 一元加号运算符+转为数字，在 JavaScript 中，一元加号运算符（+）可以用作将变量或其他值转换为数字类型的快速方法。这个运算符会尝试将其操作数转换为一个数字，如果转换失败，则结果为 NaN
  // 传统数据类型
  const toNumber = (val) => {
    const result = +val;
    plog(result);
  }
  // toNumber(null) // 0
  // toNumber(undefined) // NaN
  // toNumber(1) // 1
  // toNumber("123aa") // NaN
  // toNumber({}) // NaN
  // toNumber(true) // 1
  // toNumber(new Date()) // 该日期的时间戳

  // ES6的 BigInt 和Symbol，不可以转换
  // toNumber(10n)
  //toNumber(Symbol.for('a'))
  // plog(Symbol.for('a'))
}

{
  // 位移转为数字
  // 在 JavaScript 中，位移运算符用于对二进制数进行位移操作，有符号右移运算符 (>>) 和无符号右移运算符 (>>>)
  // >> 有符号右移运算符将数的二进制表示向右移动指定的位数，并在左侧填充符号位（即最高位，0 表示正数，1 表示负数）。这意味着对于正数，左侧会填充 0；对于负数，左侧会填充 1。 
  // >>> 无符号右移运算符也将数的二进制表示向右移动指定的位数，但无论数的符号如何，左侧都会填充 0。这意味着无论正数还是负数，其左侧都会用 0 填充。
  const toNumber = (val) => {
    const result = val >> 0
    plog(result)
  }
  const toNumber2 = (val) => {
    const result = val >>> 0
    plog(result)
  }

  toNumber(null)  // 0
  toNumber({})    // 0
  toNumber("10x") // 0
  toNumber("10")  // 10
  toNumber(Number.MAX_SAFE_INTEGER) // -1
  plog(Number.MAX_SAFE_INTEGER.toString(2), Number.MAX_SAFE_INTEGER.toString(2).length)
  plog(50 >> 1)
}

onMounted(() => {
  // console.log(0.1 + 0.2)
})
</script>

<style scoped></style>
