<template>
  <div>
    <p style="margin: 20px 0;">
      <el-button @click="setData(3)">变化数据为3条</el-button>
      <el-button @click="setData(2000)">变化数据为20002条</el-button>
      <el-button @click="setData(5000)">变化数据为5000条</el-button>
      <el-button @click="opendialog">打开</el-button>

      <el-radio-group v-model="radio" style="margin-left:30px">
        <el-radio :label="1">数据变化滚动到顶部</el-radio>
        <el-radio :label="2">数据变化滚动不滚动到顶部</el-radio>
      </el-radio-group>
    </p>
    <u-table ref="plTable" :max-height="height" use-virtual :data-changes-scroll-top="radio === 1" :row-height="rowHeight"
      border>
      <!-- <u-table-column type="index" width="100" fixed /> -->
      <u-table-column v-for="item in columns" :key="item.id" :resizable="item.resizable" :show-overflow-tooltip="item.showOverflow"
        :prop="item.prop" :label="item.label" :fixed="item.fixed" :width="item.width" />
    </u-table>
  </div>
</template>

<script>
  // const {
  //   dialog
  // } = require('electron').remote;
  // const { ipcRenderer } = window.require('electron');
  
  export default {
    data() {
      return {
        radio: 1,
        height: 400,
        rowHeight: 50,
        columns: Array.from({
          length: 10
        }, (_, idx) => ({
          prop: 'address',
          id: 'jfij' + idx,
          label: '地址' + idx,
          width: 200,
          showOverflow: false,
          fixed: idx == 0 ? true : idx == 10 - 1 ? 'right' : false
        })),
      }
    },
    mounted() {
      this.setData(500)
    },
    methods: {
      setData(num) {
        let data = Array.from({
          length: num
        }, (_, idx) => ({
          id: idx,
          date: '2016-05-03',
          name: 1,
          ab: 'u-table',
          address: '用法类似e2lement-ui ' + idx
        }))
        this.$refs.plTable.reloadData(data)
      },
      opendialog() {

        // dialog.showOpenDialog({
        //   properties: ['openFile', 'openDirectory', 'multiSelections'],
        //   filters: [{
        //       name: 'Images',
        //       extensions: ['jpg', 'png', 'gif']
        //     },
        //     {
        //       name: 'Movies',
        //       extensions: ['mkv', 'avi', 'mp4']
        //     },
        //     {
        //       name: 'Custom File Type',
        //       extensions: ['as']
        //     },
        //     {
        //       name: 'All Files',
        //       extensions: ['*']
        //     }
        //   ]
        // }).then(result => {
        //   console.log('result', result);
        // }).catch(err => {
        //   console.log('err', err);
        // })
       

      }
    }
  }
</script>
