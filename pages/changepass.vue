<template>
  <div>
    <b-container class="my-5">
      <b-row>
        <b-col cols="12">
          <h1 class="custom-title">เปลี่ยนรหัสผ่าน</h1>
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
                label="เปลี่ยนรหัสผ่าน"
                label-size="lg"
                label-class="font-weight-bold pt-0"
                class="mb-0"
              >
                <!-- Email -->
                <b-form-group
                  label="รหัสผ่าน : "
                  label-for="password"
                  label-cols-sm="3"
                  label-align-sm="right"
                >
                  <b-form-input
                    id="password"
                    v-model="form.password"
                    type="password"
                    :state="validateState('password')"
                    aria-describedby="password-live-feedback"
                    @input="$v.form.password.$touch()"
                  ></b-form-input>
                  <b-form-invalid-feedback id="password-live-feedback">
                    {{ passwordErrors.toString() }}
                  </b-form-invalid-feedback>
                </b-form-group>

                <b-form-group
                  label="ยืนยันรหัสผ่าน : "
                  label-for="confirm-password"
                  label-cols-sm="3"
                  label-align-sm="right"
                >
                  <b-form-input
                    id="confirm-password"
                    v-model="form.confirmPassword"
                    type="password"
                    :state="validateState('confirmPassword')"
                    aria-describedby="confirmPassword-live-feedback"
                    @input="$v.form.confirmPassword.$touch()"
                  ></b-form-input>
                  <b-form-invalid-feedback id="confirmPassword-live-feedback">
                    {{ passwordConfirmErrors.toString() }}
                  </b-form-invalid-feedback>
                </b-form-group>
              </b-form-group>
              <b-button variant="primary" type="submit">บันทึก</b-button>
            </b-form>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import { required, minLength, sameAs } from 'vuelidate/lib/validators'
import { API_URL } from '~/contains'

export default {
  middleware: 'auth',
  data() {
    return {
      show: true,
      form: {
        password: '',
        confirmPassword: '',
      },
      massage: '',
      error: '',
    }
  },
  validations: {
    form: {
      password: {
        required,
        minLength: minLength(6),
      },
      confirmPassword: {
        required,
        sameAsPassword: sameAs('password'),
      },
    },
  },
  computed: {
    passwordErrors() {
      const errors = []
      if (!this.$v.form.password.$dirty) {
        return errors
      }
      !this.$v.form.password.maxLength &&
        errors.push('รหัสผ่านต้องมีความยาวมากกว่า 6')
      !this.$v.form.password.required && errors.push('ต้องการ')
      return errors
    },
    passwordConfirmErrors() {
      const errors = []
      if (!this.$v.form.confirmPassword.$dirty) {
        return errors
      }
      !this.$v.form.confirmPassword.sameAsPassword &&
        errors.push('รหัสผ่านต้องเหมือนกัน')
      !this.$v.form.confirmPassword.required && errors.push('ต้องการ')
      return errors
    },
  },
  methods: {
    validateState(name) {
      const { $dirty, $error } = this.$v.form[name]
      return $dirty ? !$error : null
    },
    onSubmit(event) {
      this.savePassword()
      event.preventDefault()
    },
    async savePassword() {
      this.massage = null
      this.error = null
      try {
        this.$v.form.$touch()
        if (!this.$v.form.$anyError) {
          await this.$axios.put(API_URL.USERS + this.$auth.user.id, {
            password: this.form.password,
          })
          await this.$auth.fetchUser()
          this.message = `เปลี่ยนรหัสผ่านสำเร็จ`
          this.$toast.success('เปลี่ยนรหัสผ่านสำเร็จ')
          this.$router.push('/profile')
        }
      } catch (e) {
        const errorMessage = 'เปลี่ยนรหัสผ่านไม่สำเร็จ : '
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
