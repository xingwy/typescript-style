### **tslint**

- array-type

  ```ts
  // "array-type": [true, "array-simple"]  允许使用常规类型的T[]
  let list: number[] = [1,3,5]
  
  // "array-type": [true, "array"]  允许是用T[] T为任何类型
  let list: {number,string}[] = []
  
  // "array-type": [true, "generic"]  允许使用Array<T> T为任何类型
  let list: Array<{number,string}> = []
  
  ```

- ban-types

  ```ts
  //["Object", "Use {} instead."],
  //["String", "Use 'string' instead."],
  //["Number", "Use 'number' instead."],
  //["Boolean", "Use 'boolean' instead."]
  
  //类型替换 
  tmp: String  ×
  tmp: string  √
  ```

- class-name

  类名必需

- curly

  for if do while 要有括号 

  ```ts
  // 使用"curly": [true, "ignore-same-line"],忽略同行
  // error 
  if(true) 
       fullName = '1'
  while(true) 
       fullName = '1'
  
  // good
  if(true) fullName = 'Good'
  if(true) {
      fullName = 'Also Good'
  }
  ```

- deprecation

  使用不推荐的API时发出警告

- forin

  用for in 必须用if进行过滤

  ```ts
  let arr = []
  // error
  for(const m in arr) {
       // TODO
   }
  // good
  for(const m in arr) {
      if(m != null){
          // TODO 
      }
  }
  ```

- interface-name  *

  定义接口名称要求大写'I'开头

- jsdoc-format

  使用js注释的格式

- label-position

  不允许使用标签的语句

  ```ts
  // error
  outer:
      for (let i = 0; i < 3; i++)  {
            for ( let j = 0; j < 3; j++) {
                if( i===1 && j===1 ) break outer
               console.log(i, j)
          }
      }
  ```

- member-access

  类成员前必须声明public/private/ ,当然使用"no-public"可以省略public成员标志（建议）

  ```ts
  class AAA {
      constructor(){
      }
      name: string
      private age: number
  }
  ```

- new-parens

  使用new调用构造函数时需要使用括号

  ```ts
  // error
  let a: AAA  = new AAA
  
  // good
  let a: AAA  = new AAA()
  ```

- no-angle-bracket-type-assertion

  使用as type进行类型断言，不适用< type >

  ```ts
  // error
  let someValue: any = "this is a string"
  let strLength: number = (<string>someValue).length
  
  // good
  let someValue: any = "this is a string"
  let strLength: number = (someValue as string).length
  ```

- no-any

  不适用any类型

- no-arg

  禁止使用`arguments.callee`

- no-conditional-assignment

  在条件中不允许赋值

  ```ts
  // error
  let x: number
  if(x = 2){
      // TODO
  }
  ```

- no-conditional-assignment

  禁止在表达式中赋值

- no-construct

  不允许创建String,Number,Boolean的实例

  ```ts
  // error
  let n:number = new Number(1)
  ```

- no-debugger

  不允许使用调控器

- triple-equals

  使用=== 和 !==

  ```ts
  // error
  let name = 'Job'
  if(name == 'Job'){
      // TODO
  }
  
  // good
  let name = 'Job'
  if(name === 'Job'){
      // TODO
  }
  ```

- no-default-export *

  禁止使用export default

  ```ts
  // 不建议
  demo1.js
  export default name = 'Job'
  demo2.js
  import name from 'demo1.js'
  
  // 建议
  demo1.js
  export name = 'Job'
  demo2.js
  import {name} from 'demo1.js'
  ```

- no-duplicate-variable

  不允许对一个变量多次声明

- no-inferrable-types

  不允许在初始化的时候对boolean,string,number显示声明

  ```ts
  // error
  let name: string = 'Bob'
  
  // good
  let name: string
  name = 'Bob'
  ```

- no-namespace

  不允许使用内部模块和命名空间

- no-reference

  禁止使用/// <reference path=> 导入 ，使用import代替

- no-string-throw

  限制可以作为异常引发的内容

- no-unused-expression

  不允许在不属于赋值或比较的部分时使用新运算符,不允许在语句位置使用表达式

- no-var-keyword

  禁止使用var关键字

- object-literal-shorthand

  需要对象文本的方法和属性速记语法

- only-arrow-functions

  ```json
  "only-arrow-functions": [true, "allow-declarations", "allow-named-functions"]
  //允许箭头表达式，不需要传统表达式 ； 
  //允许独立的函数声明  ；
  //允许表达，function foo() {}但不是function() {}
  ```

- prefer-const

  建议对声明后从未修改的变量使用const声明

- radix

  使用parseInt()需要使用第二个参数  第二个参数默认是10（进制）

- semicolon

  禁止使用分号

  ```json
  "semicolon": [true, "never", "ignore-bound-class-methods"]  
  ```

- switch-default

  switch语句中需要默认大小写

- use-isnan

  不允许与值NaN进行比较



tslint.json

```json
{
  "extends": "gts/tslint.json",
  "rules": {
    "array-type": [true, "generic"],
    "arrow-return-shorthand": true,
    "ban": [true,
      {"name": "parseInt", "message": "tsstyle#type-coercion"},
      {"name": "parseFloat", "message": "tsstyle#type-coercion"},
      {"name": "Array", "message": "tsstyle#array-constructor"}
    ],
    "ban-types": [true,
      ["Object", "Use {} instead."],
      ["String", "Use 'string' instead."],
      ["Number", "Use 'number' instead."],
      ["Boolean", "Use 'boolean' instead."]
    ],
    "class-name": true,
    "curly": [true, "ignore-same-line"],
    "deprecation": true,
    "forin": true,
    "interface-name": [true, "never-prefix"],
    "jsdoc-format": true,
    "label-position": true,
    "member-access": [true, "no-public"],
    "new-parens": true,
    "no-angle-bracket-type-assertion": true,
    "no-any": true,
    "no-arg": true,
    "no-conditional-assignment": true,
    "no-construct": true,
    "no-debugger": true,
    "no-default-export": true,
    "no-duplicate-variable": true,
    "no-inferrable-types": true,
    "no-namespace": [true, "allow-declarations"],
    "no-reference": true,
    "no-string-throw": true,
    "no-unused-expression": true,
    "no-var-keyword": true,
    "object-literal-shorthand": true,
    "only-arrow-functions": [true, "allow-declarations", "allow-named-functions"],
    "prefer-const": true,
    "radix": true,
    "semicolon": [true, "never", "ignore-bound-class-methods"],   
    "switch-default": true,
    "triple-equals": [true, "allow-null-check"],
    "use-isnan": true,
    "variable-name": [
      true,
      "check-format",
      "ban-keywords",
      "allow-leading-underscore",
      "allow-trailing-underscore"
    ]
  }
}
```

