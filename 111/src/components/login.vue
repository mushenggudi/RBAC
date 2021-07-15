<template>
  <form action="">
    <div id="layout">
      <h3>RBAC</h3>
      <el-form ref="form" :model="form" label-width="60px">
         <el-form-item label="账号">
            <el-input  v-model="accountNumber1" placeholder="请输入邮箱" ></el-input>
          </el-form-item>
          <el-form-item label="密码">
             <el-input  v-model="password1" placeholder="请输入密码" show-password></el-input>
           </el-form-item>
          <el-form-item label="邀请码" v-show="type==='学生/助教登录'">
             <el-input  v-model="department" placeholder="请输入邀请码" show-password></el-input>
           </el-form-item>
      </el-form>
      <!-- <div id="logintoregist">
          <router-link to="/regist" v-show="type==='登录'" class="link">没有账号，现在去注册</router-link>
          <router-link to="/student" v-show="type==='注册'" class="link">已有账号，现在去登录</router-link>
          <router-link to="/regist" v-show="type==='学生/助教登录'" class="link">没有账号，现在去注册</router-link>
      </div>
      <div id="logintoregist">
          <router-link to="/student" v-show="type==='登录'" class="link">学生/助教登录</router-link>
          <router-link to="/login" v-show="type==='学生/助教登录'" class="link">老师登录</router-link>
      </div> -->
	  <div id="logintoregist">
	      <el-button><router-link to="/student" class="link">学生登陆</router-link></el-button>
		  <el-button><router-link to="/teacher" class="link">教师登陆</router-link></el-button>
		  <el-button><router-link to="/admin" class="link">管理员登陆</router-link></el-button>
	  </div>
    </div>
  </form>
</template>

<script>
export default {
  data: function () {
    return {
      form: { },
      accountNumber1: '',
      password1: '',
      department: ''
    }
  },
  methods: {
    Submit () {
      const accountNumber = this.accountNumber1
      const password = this.password1
      const department = this.department
      // 告诉父组件，abcEvent已经发生了
      // this.$emit('submit', {
      //   accountNumber,
      //   password,
      //   department
      // })
      console.log(accountNumber, password, department)
    }
  },
  name: 'Gform'
}
</script>

<style scoped>
#layout {
  width: 380px;
  height: 540px;
  background-color: aliceblue;
  border-radius: 5px;
  font-size: 14px;
  font-weight: 400;
  color: black
    /* grey1 (Light); grey10 (Dark); grey1 (White); grey2 (White); grey3 (White); */;
  line-height: normal;
  font-feature-settings: "kern";
  padding: 85px 40px 85px 40px;
  margin-left: 905px;
  margin-top: 95px;
}

h3 {
  text-align: left;
  font-family: PingFangSC-Semibold, "PingFang SC Semibold", "PingFang SC",
    sans-serif;
  font-size: 30px;
  font-weight: 650;
  margin-bottom: 47px;
}

#item {
  width: 300px;
  height: 48px;
  background-color: #fff;
  margin-bottom: 16px;
  padding: 12px;
  box-sizing: border-box;
  border-radius: 2px;
}

#item label {
  padding-left: 20px;
  padding-right: 20px;
  font-weight: 500;
  font-size: 14px;
  /* font-weight: 400; */
  color: #333333;
  line-height: normal;
  font-feature-settings: "kern";
  margin-right: 25px;
}

#item input {
  border-style: none;
  outline-style: none;
}

#btn {
  width: 300px;
  height: 50px;
  font-size: 16px;
  color: white;
  border-radius: 2px;
  border-style: none;
  cursor: pointer;
  margin-top: 18px;
  margin-bottom: 16px;
  text-align: center;
}

#login-regist {
  text-align: center;
}

.link {
  color:black;
  text-decoration: none;
}
#logintoregist{
	text-align: center;
  margin-top: 10px;
}

</style>
