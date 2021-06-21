<template>
  <div>
    <b-container class="my-5">
      <b-row>
        <b-col cols="12">
          <h1 class="custom-title">แก้ไขโปรไฟล์</h1>
          <hr class="my-3" />
        </b-col>
        <b-col cols="12">
          <b-button to="/profile" variant="outline-secondary">กลับ</b-button>
        </b-col>
        <b-col cols="12" class="secondary-font my-3">
          <b-card>
            <b-alert v-if="massage" show variant="success">
              {{ massage }}
            </b-alert>
            <b-alert v-if="error" show variant="danger">{{ error }}</b-alert>
            <b-form v-if="show" @submit="onSubmit">
              <b-form-group
                label-cols-lg="3"
                label="ข้อมูลผู้ใช้"
                label-size="lg"
                label-class="font-weight-bold pt-0"
                class="mb-0"
              >
                <b-form-group
                  label="อีเมล : "
                  label-for="email"
                  label-cols-sm="3"
                  label-align-sm="right"
                >
                  <b-form-input
                    id="email"
                    v-model="form.email"
                    disabled
                  ></b-form-input>
                </b-form-group>

                <b-form-group
                  label="ชื่อ : "
                  label-for="first-name"
                  label-cols-sm="3"
                  label-align-sm="right"
                >
                  <b-form-input
                    id="first-name"
                    v-model="form.firstName"
                  ></b-form-input>
                </b-form-group>

                <b-form-group
                  label="นามสกุล : "
                  label-for="last-name"
                  label-cols-sm="3"
                  label-align-sm="right"
                >
                  <b-form-input
                    id="last-name"
                    v-model="form.lastName"
                  ></b-form-input>
                </b-form-group>

                <b-form-group
                  label="เบอร์โทร : "
                  label-for="mobile"
                  label-cols-sm="3"
                  label-align-sm="right"
                >
                  <b-form-input
                    id="mobile"
                    v-model="form.mobile"
                  ></b-form-input>
                </b-form-group>

                <b-form-group
                  label="ที่อยู่ : "
                  label-for="address"
                  label-cols-sm="3"
                  label-align-sm="right"
                >
                  <b-form-textarea
                    id="address"
                    v-model="form.address"
                    rows="3"
                    max-rows="6"
                  ></b-form-textarea>
                </b-form-group>
              </b-form-group>
              <hr />
              <b-button variant="primary" type="submit">บันทึก</b-button>
            </b-form>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import { API_URL } from '~/contains'
export default {
  middleware: 'auth',
  data() {
    return {
      show: true,
      form: {
        email: this.$auth.user.email,
        firstName: this.$auth.user.first_name,
        lastName: this.$auth.user.last_name,
        mobile: this.$auth.user.mobile,
        address: this.$auth.user.address,
      },
      massage: '',
      error: '',
    }
  },
  methods: {
    onSubmit(event) {
      this.saveUser()
      event.preventDefault()
    },
    async saveUser() {
      this.massage = null
      this.error = null
      try {
        await this.$axios.put(API_URL.USERS + this.$auth.user.id, {
          username: this.form.email,
          email: this.form.email,
          first_name: this.form.firstName,
          last_name: this.form.lastName,
          mobile: this.form.mobile,
          address: this.form.address,
        })
        await this.$auth.fetchUser()
        this.message = `แก้ไขข้อมูลสำเร็จ`
        this.$toast.success('แก้ไขข้อมูลสำเร็จ')
        this.$router.push('/profile')
      } catch (e) {
        const errorMessage = 'แก้ไขข้อมูลไม่สำเร็จ : '
        if (e.response?.data?.message) {
          console.error(errorMessage + e.response?.data?.message)
          this.error = errorMessage + e.response?.data?.message
          this.$toast.error(errorMessage + e.response?.data?.message)
        } else {
          console.error(errorMessage + e)
          this.error = errorMessage + e
          this.$toast.error(errorMessage + e)
        }
      }
    },
  },
}
</script>

<style></style>
