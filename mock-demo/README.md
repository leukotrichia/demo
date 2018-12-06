1.新建一个Vue项目
$ vue init webpack mock-demo


2.安装依赖
$ cd mock-demo
$ cnpm install


3.安装mockjs
$ cnpm install --save-dev mockjs


4.启动项目
$ cnpm start


5.引入
在main.js中加入如下代码	
import Mock from 'mockjs'
//将mockjs定义为Vue的原型属性$mock
Vue.prototype.$mock = Mock


6.使用
created () {

  let data = this.$mock.mock({
  
  // 属性 list1 的值是一个数组，其中含有 1 到 10 个元素
  
  'list1|1-10': [{
  
    // 属性 id 是一个自增数，起始值为 1，每次增 1
    
    'id|+1': 1
    
  }],
  
  //属性list2的值是一个数组，其中含有10个元素
  
  'list2|10': [{
  
    //生成随机中文姓名
    
    'name': '@cname()'
    
  }]
  
  });
  
  console.log(data.list1)
  
}



