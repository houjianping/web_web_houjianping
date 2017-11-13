Vue中使用vux的配置，分为两种情况：
一、根据vux文档直接安装，无需手动配置
?
1
2
3
4
5
npm install vue-cli -g  // 如果还没安装
vue init airyland/vux2 my-project  // 创建名为 my-project 的模板
cd my-project  // 进入项目
npm install --registry=https://registry.npm.taobao.org  // 开始安装
npm run dev  // 运行项目
二、想在已创建的Vue工程里引入vue组件
<1>. 在项目里安装vux
?
1
npm install vux --save
<2>. 安装vux-loader （这个vux文档似乎没介绍，当初没安装结果报了一堆错误） 
?
1
npm install vux-loader --save-dev
<3>. 安装less-loader  （这个是用以正确编译less源码，否则会出现 ' Cannot GET / '）
?
1
npm install less less-loader --save-dev
<4>. 安装yaml-loader  (以正确进行语言文件读取, 我没安装似乎也没报错)
?
1
npm install yaml-loader --save-dev
<5>. 在build/webpack.base.conf.js 文件进行配置
?
1
2
3
4
5
6
7
const vuxLoader = require('vux-loader')
const webpackConfig = originalConfig
 
// 原来的 module.exports 代码赋值给变量 webpackConfig，
 
//即将原来的module.exports 改为 const webpackConfig
module.exports = vuxLoader.merge(webpackConfig, { plugins: ['vux-ui'] })
以上就是本文的全部内容，希望对大家的学习有所帮助，也希望大家多多支持脚本之家。
