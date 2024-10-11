<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>

<script setup>
import { onMounted, nextTick } from 'vue'
import PDFObject from 'pdfobject'

onMounted(async () => {
  const ele = document.createElement('div')
  ele.id = 'pdf_viewer'
  document.body.appendChild(ele)
  await nextTick()
  if (PDFObject.supportsPDFs) {
    PDFObject.embed('http://47.94.130.165:3002/index.pdf', '#pdf_viewer')
  } else {
    location.href = '/resume/canvas'
  }
  console.log(PDFObject)
  console.log([] + [])
  console.log(String([]))
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
