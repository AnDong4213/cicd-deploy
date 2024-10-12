<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>

<script setup>
import { onMounted, nextTick } from 'vue'
// import PDFObject from 'pdfobject'

const viewPdef = async () => {
  /* const ele = document.createElement('div')
  ele.id = 'pdf_viewer'
  document.body.appendChild(ele)
  await nextTick()
  if (PDFObject.supportsPDFs) {
    PDFObject.embed('http://47.94.130.165:3002/index.pdf', '#pdf_viewer')
  } else {
    location.href = '/resume/canvas'
  }
  console.log(PDFObject)
   */
}

const handleRegexp = () => {
  // 在JavaScript的String.prototype.replace()方法中，$1、$2、$3等是用来引用匹配结果中的捕获组（capturing groups）的，而$&是用来引用整个匹配结果的。
  // 捕获组引用（$1, $2, $3, ...）
  // 当你在正则表达式中使用括号()时，你会创建一个捕获组。匹配这个捕获组的内容可以在替换字符串中通过$1、$2、$3等来引用，其中数字表示捕获组的索引（从1开始，因为$0通常用来表示整个匹配结果，但在replace方法的替换字符串中，$&是更常用的表示整个匹配结果的方式）。
  // 在replace方法的替换字符串中，$字符具有特殊含义，用于引用匹配结果或捕获组。如果你想要在替换字符串中实际包含$字符，你需要使用$$来表示。
  /* const str = 'The quick brown fox jumps over the lazy dog'
  const regex = /(\w+)\s(\w+)/
  // console.log(str.match(regex).join(' '))
  const newStr = str.replace(regex, '$2, $1')
  console.log(newStr) // quick, The brown fox jumps over the lazy dog */

  const str = 'Hello, world!'
  const regex = /\b\w+\b/ // 匹配单词边界内的单词字符序列
  console.log(str.match(regex))
  const newStr = str.replace(regex, '$& world')
  console.log(newStr) // Hello world, world!
}

onMounted(async () => {
  // viewPdef()
  /* console.log([] + [])
  console.log(String([]))   都是 '' */
  handleRegexp()
})
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
