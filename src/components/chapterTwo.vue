<template>
  <div class="hello">Hello Vue3</div>
</template>

<script setup>
import { onMounted } from 'vue'

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
    const result = +val
    plog(result)
  }
  // toNumber(null) // 0
  // toNumber(undefined) // NaN
  // toNumber(1) // 1
  // toNumber("123aa") // NaN
  // toNumber({}) // NaN
  // toNumber(true) // 1
  // toNumber(false) // 0
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
  const aa = 15
  const aaa = '11110'

  // toNumber(null); // 0
  // toNumber({}); // 0
  // toNumber("10x"); // 0
  // toNumber("10"); // 10
  // toNumber(10n); // 报错，ES6的 BigInt 和Symbol，不可以转换
  // toNumber(Number.MAX_SAFE_INTEGER); // -1
  // toNumber2(Number.MAX_SAFE_INTEGER); // 4294967295
  // plog(aa.toString(2));
  // parseInt 是 JavaScript 中的一个全局函数，用于将一个字符串解析成整数。它尝试从字符串的开头解析一个整数，直到遇到第一个无法解析为数字的字符为止，然后返回解析得到的整数。如果字符串的第一个字符不能被解析为数字（包括正负号），则返回 NaN（Not-a-Number，非数字值）。
  // plog(parseInt(aaa, 2)); // 30
  // plog(
  //   Number.MAX_SAFE_INTEGER.toString(2),
  //   Number.MAX_SAFE_INTEGER.toString(2).length
  // );
  // plog(25 >> 1);
  // plog(25 >>> 1);
  // plog(Number.MAX_SAFE_INTEGER, 2 ** 32, Math.pow(2, 32));
}

{
  const arr = ['1', '2', '3']
  // plog(arr.map(parseInt)); // [1, NaN, NaN]
  // plog(arr.map((val, index) => parseInt(val, index))); // [1, NaN, NaN]
}

{
  // 哪些值转化为布尔值为false
  // console.log(Boolean(false)); // 输出: false
  // console.log(Boolean(0)); // 输出: false
  // console.log(Boolean(-0)); // 输出: false
  // console.log(Boolean(0n)); // 输出: false  BigInt 0（BigInt 类型的零）。
  // console.log(Boolean("")); // 输出: false
  // console.log(Boolean(null)); // 输出: false
  // console.log(Boolean(undefined)); // 输出: false
  // console.log(Boolean(NaN)); // 输出: false
  // plog(!!NaN);
}

{
  // 宽松比较，本质是 隐式转换
  // plog(0 == null); // false
  // plog(null == null); // true
  // plog(null == undefined); // true
  // plog("0" == false); // true
  // plog(Symbol.for("a") == Symbol.for("a")); // true
  // plog(Symbol("a") === Symbol("a")); // false
  // Symbol 值可以显式转为字符串。
  let sym = Symbol('My symbol')
  // plog(sym.description);
  // plog(sym.toString()); // 'Symbol(My symbol)'
  // plog(String(sym)); // 'Symbol(My symbol)'
  // plog(String(sym) === sym.toString()); // true
  // Symbol 值也可以转为布尔值，但是不能转为数值。Symbol 值不能与其他类型的值进行运算，会报错。
  // Symbol 值通过Symbol()函数生成。
  // 我们希望重新使用同一个 Symbol 值，Symbol.for()方法可以做到这一点。
  // Symbol.for()与Symbol()这两种写法，都会生成新的 Symbol。它们的区别是，前者会被登记在全局环境中供搜索，后者不会。Symbol.for()不会每次调用就返回一个新的 Symbol 类型的值，而是会先检查给定的key是否已经存在，如果不存在才会新建一个值。比如，如果你调用Symbol.for("cat")30 次，每次都会返回同一个 Symbol 值，但是调用Symbol("cat")30 次，会返回 30 个不同的 Symbol 值。
  // Symbol.for()为 Symbol 值登记的名字，是全局环境的，不管有没有在全局环境运行。

  const a = {
    valueOf() {
      return 1000
    }
  }
  const b = {
    valueOf() {
      return 100
    }
  }
  const c = {
    value: 42,
    valueOf: function () {
      return this.value
    }
  }

  // plog(a > b); // true
  // plog(a < b);
  // plog(a.valueOf());
  // plog(+a, typeof a);
  // plog(+c);
  // plog(typeof 0b111); // number
  // plog(typeof 11n); // bigint
  // plog(parseInt("111", 2) === 0b111); // true
}

{
  // typeof性能比instanceof性能高20倍？(高2-3倍，在千万级下)
  /*  var count = 10000000;
  var func = function () {};

  var startTime = new Date();
  console.log(typeof func === "function");
  for (var j = 0; j < count; j++) {
    typeof func === "function";
  }
  console.log(
    '[typeof func === "function"] ' +
      (new Date().getTime() - startTime.getTime())
  );
  startTime = new Date();

  console.log(func instanceof Function);
  for (var k = 0; k < count; k++) {
    func instanceof Function;
  }
  console.log(
    "[func instanceof Function] " + (new Date().getTime() - startTime.getTime())
  ); */
  // null 和 undefined的实现机制完全不一样，null是关键字，undefined是个变量
  // plog(Object.getOwnPropertyDescriptor(global, "null")); // undefined
  // plog(Object.getOwnPropertyDescriptor(global, "undefined"));
  // plog(Object.getOwnPropertyDescriptor(global, "Function"));
  // plog(Object.getOwnPropertyDescriptor(window, "undefined"));
  // plog(window === global); // true
}

// 2-2 综合评定，数据类型8种判断方式

{
  /* 第一种 typeof */
  // plog(typeof document.all, typeof document.all === "undefined"); // undefined，true
  // plog(typeof null); // object
  // plog(typeof NaN); // number
  // NaN，它实际上是一个数字类型的值，是数字类型的一部分，不过是一个特殊的、表示未定义或不可表示的数字，NaN 是由数字运算产生的，通常是由于无效的数学操作（如 0 除以 0）或试图将非数字字符串转换为数字时产生的。
  // console.log(isNaN(NaN)); // 输出 true
  // console.log(Number.isNaN(NaN)); // 输出 true
  // console.log(isNaN("Hello")); // 输出 true，因为 "Hello" 被转换为 NaN
  // console.log(Number.isNaN("Hello")); // 输出 false，因为 "Hello" 不是一个数字值

  /* 第二种 constructor，指向创建实例对象的构造函数 */
  // plog(constructor);  // ƒ Window() { [native code] }
  // console.log("a".constructor, typeof "a".constructor); // ƒ String() { [native code] }，'function'
  // console.log("a".constructor.name, typeof "a"); // String string
  // console.log({}.constructor.name, typeof {}); // Object object
  // console.log([].constructor.name, typeof []); // Array object
  // console.log(true.constructor.name, typeof true); // Boolean boolean
  // console.log(new Map([{}]).constructor.name, typeof new Map([{}])); // Map object
  // plog(new String("aa") == "aa"); // true

  class p1 {
    constructor() {
      this.age = 7
    }
    getAge() {}
  }

  const a1 = new p1()
  // plog(a1);
  // plog(a1.constructor.name == "p1");  // true

  /* 第三种 instanceof，它用于判断一个对象是否是某个构造函数的实例 */
  /* plog(a1 instanceof p1); // true
  plog(
    a1.__proto__ === a1.constructor.prototype,
    a1.constructor.prototype === p1.prototype,
    p1.prototype
  ); // true，true */

  /* 第四种 isPrototypeOf，isPrototypeOf 是 Object 原型链上的一个方法，检查一个实例对象是否存在于另一个对象的原型链上 */
  // 能正常返回值的情况，基本等同于instanceof，比instanceof安全些
  // eslint-disable-next-line no-prototype-builtins
  // plog(p1.prototype.isPrototypeOf(a1)); // true
  // eslint-disable-next-line no-prototype-builtins
  // plog(Object.prototype.isPrototypeOf(a1)); // true
  // eslint-disable-next-line no-prototype-builtins
  // plog(Object.prototype.isPrototypeOf(null)); // false
  // eslint-disable-next-line no-prototype-builtins
  // plog(Object.prototype.isPrototypeOf(BigInt.prototype)); // true

  /* 第五种 Object.prototype.toString */
  // 当你调用Object.prototype.toString.call(value)时，JavaScript引擎会执行以下步骤：

  // 1、获取Object.prototype上的toString方法：这个方法是一个内置的函数，用于返回表示该对象的字符串。
  // 2、使用call方法改变this的上下文：call方法允许你调用一个函数，同时指定函数体内this的值。在这个例子中，this被设置为value参数所代表的对象。
  // 3、返回类型字符串：根据value的实际类型，Object.prototype.toString会返回一个特定的字符串，比如"[object Type]"，其中Type是对象的类型名称。
  // plog(Object.prototype.toString.call(1n)); // [object BigInt]
  // plog(Object.prototype.toString.call(new Map([{}]))); // [object Map]
  // plog(Object.prototype.toString.call(Boolean.prototype));
  // plog(Object.prototype.toString("1n")); // [object Object]

  /* 第六种 鸭子类型检测 */

  /* 第七种 Symbol.toStringTag */
  // Symbol.toStringTag 是一个内置的符号（Symbol），它用于定义对象在调用 Object.prototype.toString.call(obj) 方法时返回的字符串描述。这个描述通常用于调试目的，以提供一个更易于识别的对象类型标签。
  class MyClass {
    // 自定义 toStringTag
    get [Symbol.toStringTag]() {
      return 'MyCustomClass'
    }
  }
  const obj = new MyClass()
  // console.log(Object.prototype.toString.call(obj)); // 输出: "[object MyCustomClass]"

  /* 第八种 等比较 */
  // plog(void 0); // undefined
}

// 2-3 Es6增强的NaN
{
  // plog(typeof NaN); // number
  // plog(typeof Number.NaN); // number
  // // eslint-disable-next-line use-isnan
  // plog(NaN === NaN); // false
  // plog(isNaN(Symbol())); // 报错
  // plog(Number.isNaN(Symbol())); //false 不报错
  // plog("isNaN" in Number); // true

  const arr = [NaN]
  // plog(arr.indexOf(NaN)); // -1
  // plog(arr.includes(NaN)); // true

  // Number.isNaN和isNaN
  // isNaN，它会首先尝试将参数转换为一个数字，然后再判断转换后的值是否是 NaN，
  // Number.isNaN，不会隐式地将参数转换为数字，只有当参数是 NaN 时，才返回 true

  // Object.is 是 JavaScript 中的一个方法，它用于比较两个值是否严格相等（即值和类型都相等）。这个方法与严格相等运算符 === 非常相似，但在处理某些特殊情况时有所不同。
  // plog(Object.is(NaN, NaN)); // true
  // plog(Object.is(+0, -0)); // false
  // eslint-disable-next-line no-compare-neg-zero
  // plog(+0 === -0) // true
}

// 2-4 数值千分位6种方法
{
  const num = 93876543.02
  const num1 = 93876543
  const format_with_array1 = (number) => {
    // 转为字符串，并按照.拆分
    var arr = (number + '').split('.')
    // 整数部分再拆分
    var int = arr[0].split('')
    // 小数部分
    var fraction = arr[1] || ''
    // 返回的变量
    var r = ''
    // 倒叙并遍历
    int.reverse().forEach((v, i) => {
      if (i !== 0 && i % 3 === 0) {
        r = v + ',' + r
      } else {
        r = v + r
      }
    })
    return r + (fraction ? '.' + fraction : '')
  }
  plog(format_with_array1(num))

  const format_with_array2 = (number) => {
    // 数字转字符串, 并按照 .分割
    var arr = (number + '').split('.')
    var int = arr[0] + ''
    var fraction = arr[1] || ''
    // 多余的位数
    var f = int.length % 3
    // 获取多余的位数，f可能是0， 即r可能是空字符串
    var r = int.substring(0, f)
    // 每三位添加","和对应的字符
    for (var i = 0; i < Math.floor(int.length / 3); i++) {
      r += ',' + int.substring(f + i * 3, f + (i + 1) * 3)
    }

    //多余的位数，上面
    if (f === 0) {
      r = r.substring(1)
    }
    // 整数部分和小数部分拼接
    return r + (fraction ? '.' + fraction : '')
  }
  plog(format_with_array2(num))

  // 使用正则
  // const reg = /hello (?=[a-z])+/,
  //   str = 'hello 1'
  // plog(reg.test(str))
  // plog(str.match(reg))
  // ?= 正向前瞻断言
  // ?: 非捕获组，非捕获组用于分组但不捕获匹配的文本，这可以提高正则表达式的性能，特别是在不需要捕获组内容的情况下
  /* const regex = /(?:foo|bar)baz/g
  const str = 'aasfoobaz4324barbazq'
  plog(str.match(regex)) // ['foobaz', 'barbaz'] */
  const format_with_regex = (number) => {
    var arr = (number + '').split('.')
    var int = arr[0]
    var fraction = arr[1] || ''
    // const reg = /\d{1,3}(?=(\d{3})+$)/g
    // plog(int.match(reg)) // ['93', '876']
    // return int.replace(reg, '$&,') + (fraction ? '.' + fraction : '')

    const reg = /(\d)(?=(?:\d{3})+$)/g
    plog(int.match(reg)) // ['3', '6']
    return int.replace(reg, '$1,') + (fraction ? '.' + fraction : '')
  }

  const format_with_regex2 = (number) => {
    var arr = (number + '').split('.')
    var int = arr[0]
    var fraction = arr[1] || ''
    var reg = /\d{1,3}(?=(\d{3})+$)/g
    return (
      (int + '').replace(reg, function (match, ...args) {
        // console.log(match, '--', args)
        return match + ','
      }) + (fraction ? '.' + fraction : '')
    )
  }
  plog(format_with_regex2(num))

  // plog(19 >> 2)
}

// 2-5 [] + [], [] + {}, {} + [], {} + {}

{
  // plog([] + []) // ''
  // plog([] + {}) // '[object Object]'
  /* plog({} + [])
  plog({} + {}) // [object Object][object Object]
  // 这两个在控制台下结果是不一样的，控制台下{}是一个代码块，相当于{}; + [] 和 {}; + {}
  */
  // 空数组 [] 被转换成字符串时，会变成 ""（空字符串）。
  // 空对象 {} 被转换成字符串时，会变成 "[object Object]"。这是因为在 JavaScript 中，当你尝试将一个对象转换成字符串时，默认情况下会调用对象的 toString() 方法，而普通对象的 toString() 方法会返回 "[object Object]"。
  // plog(String({}), '--', {}.toString(), '--', [].toString())
  // plog([].valueOf()) // []
  // plog(Symbol.for('2') + 9) //  TypeError: Cannot convert a Symbol value to a number
  // plog(2n + 6) // TypeError: Cannot mix BigInt and other types, use explicit conversions
}

// 2-6 综合训练

{
  console.log(2 + '2') // '22'
  console.log(true + true) // 2
  console.log(2 + [4, 5, 6]) // '24,5,6'
  console.log([4, 5, 6].toString()) // 4,5,6
}

onMounted(() => {
  // console.log(0.1 + 0.2)
  //   位：是计算机存储的最小单位，也称为比特（bit）。
  // 计算机中用二进制中的0和1来表示数据，一个0或1就代表一位。
  // n位就能代表2的n次方个值。
  // 比如1位，代表的值有
  // 1 或者 0
  // 2位就能表示四个值
  // 00  01  10  11
  function Person(name) {
    this.name = name
  }

  function Employee(name, employeeId) {
    // 调用Person构造函数，继承Person的属性
    Person.call(this, name)
    this.employeeId = employeeId
  }
  Employee.prototype = Object.create(Person.prototype)
  Employee.prototype.constructor = Employee

  const emp1 = new Employee('John Doe', 'E12345')
  // console.log(emp1)
  // console.log(emp1.constructor.name)

  function instanceOf(A, B) {
    let p = A
    while (p) {
      if (p === B.prototype) {
        return true
      }
      // p = p.__proto__;
      p = Object.getPrototypeOf(p)
    }
    return false
  }
  // plog(instanceOf(emp1, Employee))

  function test(...args) {
    console.log(args)
    console.log(typeof args)
  }
  test(15)

  console.log(typeof typeof 1) // string
})
</script>

<style scoped></style>
