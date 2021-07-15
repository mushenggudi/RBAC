<template>
	<div>
		<h1 style="text-align: center;">教师界面</h1>
		<div class="container">
		    <div id="box">
		          <el-dialog title="提示" size="small" width="30%" :append-to-body="true" :visible.sync="dialogFormVisible1" :close-on-click-modal="false">
		            <el-form style="font-size: 20px;">
		              确定要删除么？
		            </el-form>
		              <div slot="footer" class="dialog-footer" style="">
		                <el-button style="color: white;" size="medium" type="primary" @click="cancel" id="save">取消</el-button>
		                <el-button style="color: white;" size="medium" type="danger" @click="confirm1" id="save">确定</el-button>
		              </div>
		          </el-dialog>
				<div style="margin-left: 100px;">
					<el-button id="delete" @click="batchDelNotice()" type="danger" size="mini" round style="margin-left: 180px;"><i></i> 批量删除 </el-button>
					<create id="insert" v-on:listentoChildEvent="insertdata" ></create>
				</div>
		        <el-input style="width: 100%;" v-model="search" size="mini" placeholder="输入关键字搜索" />
		
		    </div>
		    <el-table
		        ref="multipleTable"
		        :data="
		            tableData.filter(
		                (data) =>
		                    !search ||
		                    data.name.toLowerCase().includes(search.toLowerCase()) ||
		                    data.age.toLowerCase().includes(search.toLowerCase()) ||
		                    data.phone.toLowerCase().includes(search.toLowerCase())
		            )
		        "
		        tooltip-effect="dark"
		        style="width: 100%"
		        max-height="500"
		        @selection-change="handleSelectionChange"
		    >
		        <el-table-column type="selection" width="55"> </el-table-column>
		        <el-table-column width="60px" align="center" type="index" :index="indexFn" label="序号"></el-table-column>
		        <el-table-column prop="name" label="名字" width="100"> </el-table-column>
		        <el-table-column prop="age" label="年龄" width="100"> </el-table-column>
		        <el-table-column prop="phone" label="联系方式" width="100" show-overflow-tooltip> </el-table-column>
		        <el-table-column label="操作" fixed="right"  width="100" align="center">
		            <template slot-scope="scope">
		                <!--单个删除按钮-->
		                <el-button style="color:white" @click.native.prevent="deleteRow(scope.$index, tableData)" type="danger" size="small"> 移除 </el-button>
		                <el-dialog title="提示" size="small" width="30%" :append-to-body="true" :visible.sync="dialogFormVisible" :close-on-click-modal="false">
		                  <el-form style="font-size: 20px;">
		                    确定要删除么？
		                  </el-form>
		                    <div slot="footer" class="dialog-footer" style="">
		                      <el-button style="color: white;" size="medium" type="primary" @click="cancel" id="save">取消</el-button>
		                      <el-button style="color: white;" size="medium" type="danger" @click="confirm(selectindex, tableData)" id="save">确定</el-button>
		                    </div>
		                </el-dialog>
		            </template>
		        </el-table-column>
		    </el-table>
		</div>
	</div>
</template>

<script>
import create from './create.vue'
export default {
  name: 'LessonTable',
  data () {
    return {
      accountNumber: '',
      search: '',
      selectionList: [],
      selectionList1: [],
      tableData: [{
		  name:"张三",
		  age:"18",
		  phone:"123456789"
	  },{
		  name:"李四",
		  age:"18",
		  phone:"123456789"
	  },{
		  name:"王五",
		  age:"18",
		  phone:"123456789"
	  },{
		  name:"金六",
		  age:"18",
		  phone:"123456789"
	  },
      ],
      multipleSelection: '',
      dialogFormVisible: false,
      dialogFormVisible1: false,
      selectindex: ''
    }
  },
  components: {
    create
  },
  created () {
    // const da = this.$route.query.a
    // this.accountNumber = da
    // window.a = this
    // this.accountNumber = localStorage.getItem('account')
    // this.$axios.post('Course/queryByTe', { creator: { accountNumber: this.accountNumber } })
    //   .then(res => {
    //     const { data } = res
    //     const a = data
    //     for (let i = 0; i < a.length; i++) {
    //       this.$axios.post('Time/query', { cs: { courseNum: a[i].courseNum }, statue: '1' })
    //         .then(resp => {
    //           const { data } = resp
    //           const b = data
    //           const table = { class: a[i].courseName, courseNum: a[i].courseNum, starttime: b.startTime, endtime: b.endTime }
    //           this.tableData.push(table)
    //         })
    //     }
    //   })
  },
  methods: {
    // 取消选择
    toggleSelection (rows) {
      if (rows) {
        rows.forEach((row) => {
          this.$refs.multipleTable.toggleRowSelection(row)
        })
      } else {
        this.$refs.multipleTable.clearSelection()
      }
    },
    // 将已选择行的index传入selectionlist中
    handleSelectionChange (selection) {
      this.selectionList = []
      selection.forEach((element) => {
        this.selectionList.push(element.courseNum)
      })
    },
    cancel () {
      this.$message.success('取消成功')
      this.dialogFormVisible = false
      this.dialogFormVisible1 = false
    },
    // 单行删除
    deleteRow (index, rows) {
      this.dialogFormVisible = true
      this.selectindex = index
    },
    confirm (index, rows) {
      index = this.selectindex
      // this.$axios.post('Course/delete', { courseNum: rows[index].courseNum })
      //   .then(res => {
      //     console.log(res)
      //   })
      // this.$axios.post('Time/deleteAll', { cs: { courseNum: rows[index].courseNum } })
      //   .then(res => {
      //     console.log(res)
      //   })
      // this.$axios.post('AST/deleteByCs', { cs: { courseNum: rows[index].courseNum } })
      //   .then(res => {
      //     console.log(res)
      //   })
      // this.$axios.post('CTS/deleteByCs', { cs: { courseNum: rows[index].courseNum } })
      //   .then(res => {
      //     console.log(res)
      //   })
      // this.$axios.post('DBT/deleteAll', { cs: { courseNum: rows[index].courseNum } })
      //   .then(res => {
      //     console.log(res)
      //   })
      // this.$axios.post('DBT/deleteAll1', { cs: { courseNum: rows[index].courseNum } })
      //   .then(res => {
      //     console.log(res)
      //   })
      // this.$axios.post('homet/deleteByCs', { course: { courseNum: rows[index].courseNum } })
      //   .then(res => {
      //     console.log(res)
      //   })
      // this.$axios.post('link/deleteAll', { course: { courseNum: rows[index].courseNum } })
      //   .then(res => {
      //     console.log(res)
      //   })
      rows.splice(this.selectindex, 1)
      this.selectindex = ''
      this.dialogFormVisible = false
      this.$message.success('删除成功')
    },
    // 多行删除
    batchDelNotice () {
      console.log(this.selectionList)
      this.selectionList1 = this.selectionList
      if (this.selectionList.length === 0) alert('请勾选')
      else {
        this.dialogFormVisible1 = true
      }
    },
    confirm1 () {
      const a = []
      console.log(this.selectionList)
      for (let i = 0; i < this.selectionList1.length; i++) {
        const n = i
        for (let j = n; j < this.tableData.length; j++) {
          if (this.selectionList1[i] === this.tableData[j].courseNum) {
            a.push(this.tableData[j])
          }
        }
      }
      const difference = a.filter((x) => this.tableData.indexOf(x) === -1).concat(this.tableData.filter((x) => a.indexOf(x) === -1))
      // for (let b = 0; b < a.length; b++) {
      //   this.$axios.post('Course/delete', { courseNum: a[b].courseNum })
      //     .then(res => {
      //       console.log(res)
      //     })
      //   this.$axios.post('Time/deleteAll', { cs: { courseNum: a[b].courseNum } })
      //     .then(res => {
      //       console.log(res)
      //     })
      //   this.$axios.post('AST/deleteByCs', { cs: { courseNum: a[b].courseNum } })
      //     .then(res => {
      //       console.log(res)
      //     })
      //   this.$axios.post('CTS/deleteByCs', { cs: { courseNum: a[b].courseNum } })
      //     .then(res => {
      //       console.log(res)
      //     })
      //   this.$axios.post('DBT/deleteAll', { cs: { courseNum: a[b].courseNum } })
      //     .then(res => {
      //       console.log(res)
      //     })
      //   this.$axios.post('DBT/deleteAll1', { cs: { courseNum: a[b].courseNum } })
      //     .then(res => {
      //       console.log(res)
      //     })
      //   this.$axios.post('homet/deleteByCs', { course: { courseNum: a[b].courseNum } })
      //     .then(res => {
      //       console.log(res)
      //     })
      //   this.$axios.post('link/deleteAll', { course: { courseNum: a[b].courseNum } })
      //     .then(res => {
      //       console.log(res)
      //     })
      // }
      this.tableData = difference
      this.dialogFormVisible1 = false
      this.selectionList1 = []
      this.$message.success('取消成功')
    },
    // 插入数据，从子组件中接收数据
    insertdata (data) {
      const a = { name: data.name, age: data.age, phone: data.phone}
      this.tableData.push(a)
    },
    // 序号自动增加
    indexFn (index) {
      index = index + 1
      return index
    },
    changePage (index) {
      localStorage.setItem('course', this.tableData[index].courseNum)
      this.$router.push({
        path: '/courseinfo'
      })
    }
  }
}
</script>

<style scoped>
#box {
    position: relative;
}
#delete {
    position: absolute;
}
#cancel {
    position: absolute;
    margin-left: 200px;
}
.container{
  width: 600px;
  margin-top: 200px;
  margin-left: 450px;
}
#tips{
  height: 30px;
}
</style>
