<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model="name"/>
    </div>
    <div>
      <span>年龄:</span>
      <input type="number" v-model="age"/>
    </div>
    <div>
      <span>性别:</span>
      <select v-model="sex">
        <option value="男">男</option>
        <option value="女">女</option>
      </select>
    </div>
    <div>
      <button @click="change1?addFn:chan">添加/修改</button>
    </div>
    <div>
      <table
        border="1"
        cellpadding="10"
        cellspacing="0"
      >
        <tr v-for="(item,index) in arr" :key="index">
          <th>{{index+1}}</th>
          <th>{{item.name}}</th>
          <th>{{item.age}}</th>
          <th>{{item.sex}}</th>
          <th>
            <button @click="del(index)">删除</button>
            <button @click="change(index)">编辑</button>
          </th>
        </tr>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  data(){
    return {
      change1:true,
      name:'',
      age:0,
      sex:'',
      idd:0,
      arr:[
        {name:'小赵',age:'18',sex:'女'},
        {name:'小钱',age:'19',sex:'男'},
        {name:'小孙',age:'20',sex:'女'},
        {name:'小李',age:'21',sex:'男'},
        {name:'小张',age:'22',sex:'女'},
      ]
    }
  },
  methods:{
    addFn(){
      if(this.name==''||this.age==0) {return alert('能不能行啊')}
      this.arr.push({
        name:this.name,
        age:this.age,
        sex:this.sex,
      })
    },
    del(val){
      this.arr.splice(val, 1)
    },
    change(index){
      this.name=this.arr[index].name,
      this.age=this.arr[index].age,
      this.sex=this.arr[index].sex
      this.change1=!this.change1
      this.idd=index
    },
    chan(idd){
      this.arr.splice(idd,1,{
        name:this.name,
        age:this.age,
        sex:this.sex
      })
    }
  }
}
</script>
