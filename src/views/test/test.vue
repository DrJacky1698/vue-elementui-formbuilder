<template>
  <div>
    <draggable tag="el-row" :list="list2"  :group="{ name: 'group2', pull: 'clone', put: false, revertClone: true}" :sort="false">
      <el-col :span="12" v-for="e in list2" :key="e.name">
        <el-image style="width: 100px; height: 100px;" :src="url" :fit="fit">
          <div slot="error" >
            {{e.name}}
          </div>
        </el-image>
      </el-col>
    </draggable>
    <!-- <draggable tag="el-collapse" :list="list1" :component-data="getComponentData()" :group="{ name: 'group', pull: 'clone', put: true, revertClone: true }">
        <el-collapse-item v-for="e in list1" :title="e.title" :name="e.name" :key="e.name">
          <div>{{e.description}}</div>
        </el-collapse-item>
    </draggable> -->

    <draggable tag="el-form" :component-data="getComponentData2()" :group="{ name: 'group2', pull: 'clone', put: false, revertClone: true}" :sort="false">
      <el-form-item label="活动名称">
        <el-input v-model="form.name"></el-input>
      </el-form-item>
      <el-form-item label="活动区域">
        <el-select v-model="form.region" placeholder="请选择活动区域">
          <el-option label="区域一" value="shanghai"></el-option>
          <el-option label="区域二" value="beijing"></el-option>
        </el-select>
      </el-form-item>
    </draggable>

    <draggable tag="el-form" :component-data="getComponentData2()" :group="{ name: 'group2', pull: 'clone', put: true, revertClone: true }">
      <el-form-item label="活动名称">
        <el-input v-model="form.name"></el-input>
      </el-form-item>
      <el-form-item label="活动区域">
        <el-select v-model="form.region" placeholder="请选择活动区域">
          <el-option label="区域一" value="shanghai"></el-option>
          <el-option label="区域二" value="beijing"></el-option>
        </el-select>
      </el-form-item>
    </draggable>
  </div>
</template>

<script>
import draggable from 'vuedraggable';

export default {
  components: {
    'draggable':draggable
  },
  data () {
    return {
      list1:[{title:'a',name:'a'},{title:'b',name:'b'},{title:'c',name:'c'},{title:'d',name:'d'},{title:'e',name:'e'},{title:'f',name:'f'},{title:'g',name:'g'}],
      list2:[{title:'a',name:'a'},{title:'b',name:'b'},{title:'c',name:'c'},{title:'d',name:'d'},{title:'e',name:'e'},{title:'f',name:'f'},{title:'g',name:'g'}],
      form:{}
    }
  },
  methods: {
    handleChange() {
      console.log('changed');
    },
    inputChanged(value) {
      this.activeNames = value;
    },
    getComponentData() {
      return {
        on: {
          change: this.handleChange,
          input: this.inputChanged
        },
        attrs:{
          wrap: true
        },
        props: {
          value: this.activeNames
        }
      };
    },
    getComponentData2(){
      return{
        props:{
          model:this.form
        }
      }
    }
  }
}
</script>

<style>

</style>