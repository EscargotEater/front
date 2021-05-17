<template>
  <div class="box">
    <p class="bigmsg">ระบบลงทะเบียน</p>
    <hr class="solid" />

    <p class="desc">กรุณากรอกข้อมูลเพื่อทำการลงทะเบียน</p>

    <p class="fieldname">อีเมล</p>
    <b-input-group class="mb-2" size="lg">
      <b-input-group-prepend is-text>
        <b-icon icon="envelope-fill"></b-icon>
      </b-input-group-prepend>
      <b-form-input
        v-model="register.email"
        class="msg"
        type="text"
        placeholder="โปรดกรอกอีเมลของท่านลงในช่องนี้"
      ></b-form-input>
    </b-input-group>

    <p class="fieldname">รหัสผ่าน</p>
    <b-input-group class="mb-2" size="lg">
      <b-input-group-prepend is-text>
        <b-icon icon="person-fill"></b-icon>
      </b-input-group-prepend>
      <b-form-input
        v-model="register.password"
        class="msg"
        type="text"
        placeholder="โปรดกรอกรหัสผ่านของท่านลงในช่องนี้"
      ></b-form-input>
    </b-input-group>

    <p class="fieldname">ยืนยันรหัสผ่าน</p>
    <b-input-group class="mb-2" size="lg">
      <b-input-group-prepend is-text>
        <b-icon icon="person-fill"></b-icon>
      </b-input-group-prepend>
      <b-form-input
        class="msg"
        type="text"
        placeholder="โปรดยืนยันรหัสผ่านของท่านลงในช่องนี้"
      ></b-form-input>
    </b-input-group>

    <b-button
      type="submit"
      value="submit"
      variant="outline-warning"
      style="
        display: block;
        font-family: 'K2D', sans-serif;
        font-size: 20px;
        font-weight: bold;
        letter-spacing: 0.5px;
        border-width: 3px;
        border-radius: 5px;
        transition-duration: 0.4s;
        padding: 10px 15px;
        margin-left: auto;
        margin-right: auto;
        margin-top: 20px;
        text-align: center;
      "
      @click="regis"
    >
      ลงทะเบียน
    </b-button>
    <div class="login">
      มีบัญชีอยู่แล้ว? <nuxt-link to="/login">เข้าสู่ระบบ</nuxt-link>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  layout: 'headerguest',
  data() {
    return {
      register: {
        email: '',
        password: '',
        error: null,
      },
    }
  },
  methods: {
    async regis(e) {
      e.preventDefault()
      try {
        const response = await axios.post(
          'http://localhost:1337/auth/local/register',
          this.register
        )
        this.error = response.message
      } catch (e) {
        console.log('Exception: ', e.response)
      }
    },
  },
}
</script>

<style>
/* import font Kanit */
@import url('https://fonts.googleapis.com/css2?family=Kanit:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
/* import font K2D */
@import url('https://fonts.googleapis.com/css2?family=K2D:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800&display=swap');
.bigmsg {
  color: darkslategray;
  font-family: 'K2D', sans-serif;
  font-size: 40px;
  text-align: center;
  padding-top: 120px;
  font-weight: bold;
}
.box {
  margin: auto;
  width: 60%;
  padding: 10px;
}
.desc {
  color: black;
  font-family: 'K2D', sans-serif;
  font-size: 25px;
  font-weight: bold;
  margin-top: 30px;
  text-align: center;
}
.fieldname {
  margin-top: 20px;
  color: darkslategray;
  font-family: 'K2D', sans-serif;
  font-size: 20px;
}
.login {
  font-family: 'K2D', sans-serif;
  font-size: 20px;
  font-weight: bold;
  margin-top: 20px;
  text-align: center;
}
.msg {
  font-family: 'K2D', sans-serif;
  font-size: 20px;
}
</style>
