<template>
  <div class="form_reg">
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group
        id="input-group-1"
        label="Email"
        label-for="input-1"
      >
        <b-form-input
          id="input-1"
          v-model="form.email"
          type="email"
          required=""
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-2" label="Пароль" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.name"
          required=""
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-4">
        <b-form-checkbox-group v-model="form.checked" id="checkboxes-4">
          <b-form-checkbox value="me">Запомнить меня</b-form-checkbox>
        </b-form-checkbox-group>
      </b-form-group>
      <b-button type="submit" variant="dark">Войти</b-button>
    </b-form>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        form: {
            email: '',
            name: '',
            checked: []
        },
        show: true
      }
    },
    methods: {
      onSubmit(evt) {
        evt.preventDefault()
        alert(JSON.stringify(this.form))
      },
      onReset(evt) {
        evt.preventDefault()
        // Reset our form values
        this.form.email = ''
        this.form.name = ''
        this.form.checked = []
        // Trick to reset/clear native browser form validation state
        this.show = false
        this.$nextTick(() => {
        this.show = true
      })
    }
  }
}
</script>

