<template>
  <div class="header">
    <div class="logo">仟嘉利健康商城</div>
    <div class="user-info">
      <el-dropdown trigger="click" @command="handleCommand">
        <span class="el-dropdown-link">
          <img class="user-logo" src="../../assets/image/img.jpg"> {{username}}
        </span>
        <el-dropdown-menu slot="dropdown">
          <el-dropdown-item command="loginout">退出</el-dropdown-item>
        </el-dropdown-menu>
      </el-dropdown>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: ''
    }
  },
  computed: {
    username() {
      let username = this.$storage.get('username');
      return username ? username : this.name;
    }
  },
  methods: {
    handleCommand(command) {
      if (command == 'loginout') {
        this.$storage.clearAll()
        this.$router.push('/login')
      }
    }
  }
}
</script>
<style scoped>
.header {
  position: relative;
  box-sizing: border-box;
  width: 100%;
  height: 70px;
  font-size: 22px;
  line-height: 70px;
  color: #fff;
}

.header .logo {
  float: left;
  width: 250px;
  text-align: center;
}

.user-info {
  float: right;
  padding-right: 50px;
  font-size: 16px;
  color: #fff;
}

.user-info .el-dropdown-link {
  position: relative;
  display: inline-block;
  padding-left: 50px;
  color: #fff;
  cursor: pointer;
  vertical-align: middle;
}

.user-info .user-logo {
  position: absolute;
  left: 0;
  top: 15px;
  width: 40px;
  height: 40px;
  border-radius: 50%;
}

.el-dropdown-menu__item {
  text-align: center;
}

@media screen and (max-width: 750px) {
  .header {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 70px;
    font-size: 16px;
    z-index: 100;
  }
  .header .logo {
    box-sizing: border-box;
    padding-left: 15px;
    width: 100px;
    height: 70px;
    white-space: nowrap;
  }
  .user-info {
    padding-right: 15px;
  }
}
</style>
