<template>
  <div class="app-container">
    <div v-if="user.Account">
      <el-row :gutter="20">

        <el-col :span="6" :xs="24">
          <user-card :user="user" />
        </el-col>

        <el-col :span="18" :xs="24">
          <el-card>
            <el-tabs v-model="activeTab">
              <el-tab-pane label="登陆记录" name="timeline">
                <timeline />
              </el-tab-pane>
              <el-tab-pane label="修改密码" name="account">
                <account />
              </el-tab-pane>
              <el-tab-pane label="谷歌二步验证" name="Googletwo">
                <googletwo />
              </el-tab-pane>
            </el-tabs>
          </el-card>
        </el-col>

      </el-row>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import UserCard from './components/UserCard'
import Googletwo from './components/Googletwo'
import Timeline from './components/Timeline'
import Account from './components/Account'

export default {
  name: 'Profile',
  components: { UserCard, Googletwo, Timeline, Account },
  data() {
    return {
      user: {},
      activeTab: 'timeline'
    }
  },
  computed: {
    ...mapGetters([
      'userinfo'
    ])
  },
  created() {
    this.getUser()
  },
  methods: {
    getUser() {
      this.user = this.userinfo
    }
  }
}
</script>
