# webpack 核心知识
* Loader  
在webpack的配置文件中对module的打包做了配置，如打包jpg文件，可以在配置文件中添加打包规则，使用Loader打包。    
![Image](https://github.com/HULLzzz/front-end/blob/master/webpack/picture/1.png)
  * url-loader
  可以将图片转化为base64的形式打包至bundle.js文件中，优点：页面加载js文件的时候不需要额外请求图片的地址。缺点：如果图片太大，会导致js文件过大，加载慢，适用于较小的图片打包。图片很大时，使用file-loader更合适，页面能快速加载完毕bundle.js。
  ![Image](https://github.com/HULLzzz/front-end/blob/master/webpack/picture/2.png)
 * plugins打包方式  
 htmlWebpackPlugins会在打包结束后自动生成一个html文件，并将打包生成的js文件自动引入到这个html文件中。
 * 使用Babel处理ES6语法
 Babel可以将ES6语法转换为ES5语法
 
 


