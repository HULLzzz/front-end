# webpack简介
`webpack is a moudle bundler.它是一个模块打包工具。`  
* CommonJS模块引入规范和ES Module模块引入方式
  * CommonJS  
  CommonJS模块是对象，是运行时加载，运行时才把模块挂载在exports之上（加载整个模块的所有），加载模块其实就是查找对象属性。CommonJS 模块输出的是一个值的拷贝，ES6 模块输出的是值的引用。 CommonJS 加载的是一个对象（即module.exports属性），该对象只有在脚本运行完才会生成。而 ES6 模块不是对象，它的对外接口只是一种静态定义，在代码静态解析阶段就会生成。
  ```
  导出使用module.exports，导入使用require('...')，绝对路径和相对路径均可，默认引用js文件，可以不写.js后缀。
  ```
  * ES Module  
  ES Module不是对象，是使用export显示指定输出，再通过import输入。此法为编译时加载，编译时遇到import就会生成一个只读引用。等到运行时就会根据此引用去被加载的模块取值。所以不会加载模块所有方法，仅取所需。   
  export之后只接声明和语句，输入使用import。   
  ```
  // 报错1
  export 1;
  // 报错2
  const m = 1;
  export m;

  // 接口名与模块内部变量之间，建立了一一对应的关系
  // 写法1
  export const m = 1;
  // 写法2
  const m = 1；
  export { m };
  // 写法3
  const m = 1；
  export { m as module };

  // 类似于对象解构
  // module.js
  export const m = 1;
  // index.js
  // 注意，这里的m得和被加载的模块输出的接口名对应
  import { m } from './module';
  // 若是想为输入的变量取名
  import { m as m1 }  './module';
  // 值得注意的是，import是编译阶段，所以不能动态加载，比如下面写法是错误的。因为'a' + 'b'在运行阶段才能取到值，运行阶段在编译阶段之后
  import { 'a' + 'b' } from './module';
  // 若是只是想运行被加载的模块，如下
  // 值得注意的是，即使加载两次也只是运行一次
  import './module';
  // 整体加载
  import * as module from './module';
  
  //输出export default
  //export与export default均可用于导出常量、函数、文件、模块等，在一个文件或模块中，export、import可以有多个，export default仅有一个export方式只能具名导入，在导入时要加{ }；export default则只能匿名导入。
  // module.js
  // 其实export default就是export { xxx as default }
  const m = 1；
  export default m;
  ===
  export { m as default }
  // index.js
  // 对应的输入也得相应变化
  import module from './module';
  ===
  import { default as module } from './module';
  
  //动态加载import 由于是编译时加载，所以不能动态加载模块，但是import方法返回是Promise对象，可以使用.then catch
  // 普通写法
  import('./module').then(({ a }) => {})
  // async、await
  const { a } = await import('./module');
  ```
