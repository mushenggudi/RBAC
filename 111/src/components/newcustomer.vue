<template>
<div id="form">
  <el-button id="create" @click="dialogFormVisible = true" size="mini" round>新增用户</el-button>
<div>
  <el-dialog title="新增学生" width="30%" :visible.sync="dialogFormVisible" :close-on-click-modal="false">
    <!-- <el-form :model="form">
      <el-form-item label="活动名称" :label-width="formLabelWidth">
        <el-input v-model="form.name" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="活动区域" :label-width="formLabelWidth">
        <el-select v-model="form.region" placeholder="请选择活动区域">
          <el-option label="区域一" value="shanghai"></el-option>
          <el-option label="区域二" value="beijing"></el-option>
         </el-select>
      </el-form-item>
    </el-form> -->
    <el-form >
      <el-form-item label="用户名" :label-width="formLabelWidth">
        <el-input style="width: 80%;" type="textarea" autosize placeholder="用户名" v-model="name" autocomplete="off"></el-input>
    </el-form-item>
    </el-form>
    <el-form >
      <el-form-item label="角色" :label-width="formLabelWidth">
        <el-input style="width: 80%;" type="textarea" autosize placeholder="角色" v-model="role" autocomplete="off"></el-input>
    </el-form-item>
    </el-form>
    <div slot="footer" class="dialog-footer">
      <el-button size="medium" type="primary" plain @click="savelesson" id="save">保存</el-button>
    </div>
  </el-dialog>
</div>
</div>
</template>

<script>
export default {
  name: 'newcus',
  data () {
    return {
      dialog: false,
      name: '',
      role: '',
      dialogTableVisible: false,
      dialogFormVisible: false,
      formLabelWidth: '120px',
      value: '',
      value1: ''
      // table: { lesson: '', starttime: '', endtime: '' }
    }
  },
  methods: {
    savelesson () {
      // const a = this.value.toString()
      // const year = a[11] + a[12] + a[13] + a[14]
      // let month = a[4] + a[5] + a[6]
      // switch (month) {
      //   case 'Jan' : month = '01'
      //     break
      //   case 'Feb' : month = '02'
      //     break
      //   case 'Mar' : month = '03'
      //     break
      //   case 'Apr' : month = '04'
      //     break
      //   case 'May' : month = '05'
      //     break
      //   case 'Jun' : month = '06'
      //     break
      //   case 'Jul' : month = '07'
      //     break
      //   case 'Aug' : month = '08'
      //     break
      //   case 'Sep' : month = '09'
      //     break
      //   case 'Oct' : month = '10'
      //     break
      //   case 'Nov' : month = '11'
      //     break
      //   case 'Dec' : month = '12'
      //     break
      //   default : month = ''
      // }
      // const day = a[8] + a[9]
      // const x = year + '-' + month + '-' + day
      // const b = this.value1.toString()
      // const year1 = b[11] + b[12] + b[13] + b[14]
      // let month1 = b[4] + b[5] + b[6]
      // switch (month1) {
      //   case 'Jan' : month1 = '01'
      //     break
      //   case 'Feb' : month1 = '02'
      //     break
      //   case 'Mar' : month1 = '03'
      //     break
      //   case 'Apr' : month1 = '04'
      //     break
      //   case 'May' : month1 = '05'
      //     break
      //   case 'Jun' : month1 = '06'
      //     break
      //   case 'Jul' : month1 = '07'
      //     break
      //   case 'Aug' : month1 = '08'
      //     break
      //   case 'Sep' : month1 = '09'
      //     break
      //   case 'Oct' : month1 = '10'
      //     break
      //   case 'Nov' : month1 = '11'
      //     break
      //   case 'Dec' : month1 = '12'
      //     break
      //   default : month1 = ''
      // }
      // const day1 = b[8] + b[9]
      // const y = year1 + '-' + month1 + '-' + day1
      // this.$axios.post('Course/query', { courseNum: this.course })
      //   .then(res => {
      //     const { data } = res
      //     if (this.course === '') {
      //       this.$message.error('请输入课程号')
      //     }
      //     if (data !== '') {
      //       this.$message.error('该课程号已存在')
      //     }
      //     if (data === '' && this.course !== '') {
      //       this.$axios.post('Course/save', { courseNum: this.course, courseName: this.lesson, coursePlace: this.area, teachPlan: this.plan, bibliography: this.book, creator: { accountNumber: this.accountNumber } })
      //         .then(res => {
      //           console.log(res)
      //         })
      //       this.$axios.post('Time/save', { cs: { courseNum: this.course }, week: this.Firstweek, specificTime: this.Firstnum, startTime: x, endTime: y, statue: '1' })
      //         .then(res => {
      //           console.log(res)
      //         })
      //       this.$axios.post('Time/save', { cs: { courseNum: this.course }, week: this.Lastweek, specificTime: this.Lastnum, startTime: x, endTime: y, statue: '2' })
      //         .then(res => {
      //           console.log(res)
      //         })
            const table = { name: this.name,role: this.role }
            this.$emit('listentoChildEvent', table)
            this.dialogFormVisible = false
            this.name = ''
			this.role = ''
            this.value = ''
            this.value1 = ''
          },
    handleClose (done) {
      this.$confirm('确认关闭？')
        .then(() => {
          done()
        })
        .catch(() => {})
    }
  }
}
</script>

<style scoped>
#create{
  margin-left:100px
}
</style>
