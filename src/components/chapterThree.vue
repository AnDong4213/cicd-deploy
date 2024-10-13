<template>
  <div class="hello">Hello Vue3</div>
</template>

<script setup>
import { onMounted } from 'vue'
const log = console.log
const hasOwn = Object.hasOwnProperty

// 3-1 通过普通属性，排序属性和隐藏类提升对象属性认知
{
  var obj = {}

  obj.p1 = 'str1'
  obj.p6 = 'str6'
  obj.p2 = 'str2'

  obj[1] = 'num1'
  obj[6] = 'num6'
  obj[2] = 'num2'
  obj[22] = 'num22'

  /* for (var p in obj) {
    console.log('property:', obj[p])
  } */
}

// 3-2 必修知识：属性来源，属性访问控制，属性冻结等等
{
  class Person {
    constructor(name, age) {
      this.name = name
      this.age = age
    }

    getName = () => {
      return this.name
    }

    getAge() {
      return this.age
    }
  }

  const person = new Person()
  // eslint-disable-next-line no-prototype-builtins
  // log(person.hasOwnProperty('getAge'))
  // log(Object.hasOwnProperty.call(person, 'getName'), Object.hasOwnProperty.call(person, 'getAge')) // true false
  // log('getAge' in person) // true
  /* for (var p in person) {
    console.log('key:', p)
  }
  log(Object.keys(person)) // ['getName', 'name', 'age'] 和 for ... in循环一样 */
  // eslint-disable-next-line no-prototype-builtins
  // log(Object.getPrototypeOf(person).hasOwnProperty('name')) // false
  // eslint-disable-next-line no-prototype-builtins
  // log(Object.getPrototypeOf(person).hasOwnProperty('getAge')) // true

  const obj = {}
  Object.defineProperty(obj, 'name', {
    configurable: true,
    enumerable: true,
    value: '小炜',
    writable: true
  })
  log(obj)
  const desc = Object.getOwnPropertyDescriptor(obj, 'name')
  log(desc)
  // log(Object.keys(obj))  // 如果enumerable为false，Object.keys 或 for ... in循环获取不到
  // delete obj.name  // 设置configurable为false，删除报错
  obj.name = '看看'
}

onMounted(() => { })
</script>

<style scoped></style>
