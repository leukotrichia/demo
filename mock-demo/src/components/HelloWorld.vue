<template>
  <div class="hello">
    <Button type="primary" @click="getTableData">随机生成数据</Button>
    <Card>
      <Table :columns="columns" :data="list"></Table>
    </Card>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      count: 10,
      list: [],
      columns: [
        {title:'编号', key:'id'},
        {title:'姓名', key: 'name'},
        {title:'地址', key: 'address'},
        {title:'生日', key: 'birth'},
        {title:'email', key: 'email'},
        {title:'面积', key: 'area'},
        {title:'金额', key: 'money'},
        {title:'备注', key: 'remark'},
        ]
    }
  },
  methods: {
    getTableData () {
      let data = this.$mock.mock({
        // 属性 list1 的值是一个数组，其中含有 10 个元素
        'list|20': [{
          // 属性 id 是一个自增数，起始值为 1，每次增 1
          'id|+1': 1,
          //生成随机中文姓名
          name: '@cname()',
          address: '@county(true)',
          birth: '@date()',
          email: '@email()',
          area: '@float(40,200,2,2)',
          money: '@float(0,9999,2,2)',
          remark: '@cword(0,10)'
        }
        ]
      });
      this.list = data.list
    }
  },
  created () {
    this.getTableData()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
