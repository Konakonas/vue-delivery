<template lang="pug">
div
  .form-left-decoration
  .form-right-decoration
  .circle
  div(v-if='!accept' class="decor form-inner")
    p
      label(for='name')  
      input#name(v-model='name' type='text' name='name' placeholder="ФИО")
    p
      label(for='email') 
      input#email(type='email' name='email' required='' v-model='email' placeholder="Email")
    p
      label(for='mobile')
      input#mobile(type='number' name='mobile' required='' v-model='mobile' placeholder="Номер телефона")
    p
      label(for='comment')  
      textarea#comment(type='textarea' name='comment' v-model='comment' placeholder="Комментарий")
    div
        p
            label(for='checkbox' class="text") Согласие на обработку персональных данных
            input#checkbox(type='checkbox' name='checkbox' v-model='checkbox' class="checkbox")
    p
      input(type='submit' value='Отправить' v-on:click='onClick')
  div(v-else='' class="decor form-inner")
    h2 Информация о доставке:
    h4(class="text") ФИО: {{name}}
    h4(class="text") Email: {{email}}
    h4(class="text") Телефон: {{mobile}}
    h4(v-if="comment" class="text") Комментарий: {{comment}}
</template>

<script>
export default {
  name: 'Home',
  data() {
      return {
        errors: [],
        name: null,
        email: null,
        mobile: null,
        comment: null,
        checkbox: null,
        accept: false,
    }
  },
  methods: {
      onClick() {
        if (!this.name || !this.email || !this.mobile) {
        alert("Заполните поля");
      }
        else if (!this.checkbox) {
        alert("Подтвердите согласие на обработку персональных данных");
      }
        else if (!this.validEmail(this.email)) {
        this.errors.push('Укажите корректный адрес электронной почты.');
      }
        else {
            this.accept = true;
        }
      },
    checkForm(e) {
      this.errors = [];
      e.preventDefault();
    },
    validEmail(email) {
      var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    }
  }
}

</script>

<style scoped>
.form-left-decoration,
.form-right-decoration {
  content: "";
  position: absolute;
  width: 50px;
  height: 20px;
  background: #f69a73;
  border-radius: 20px;
}
.form-left-decoration {
  bottom: 60px;
  left: -30px;
}
.form-right-decoration {
  top: 60px;
  right: -30px;
}
.form-left-decoration:before,
.form-left-decoration:after,
.form-right-decoration:before,
.form-right-decoration:after {
  content: "";
  position: absolute;
  width: 50px;
  height: 20px;
  border-radius: 30px;
  background: white;
}
.form-left-decoration:before {top: -20px;}
.form-left-decoration:after {
  top: 20px;
  left: 10px;
}
.form-right-decoration:before {
  top: -20px;
  right: 0;
}
.form-right-decoration:after {
  top: 20px;
  right: 10px;
}
.circle {
  position: absolute;
  bottom: 80px;
  left: -55px;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: white;
}
.form-inner {padding: 50px;}
.form-inner input,
.form-inner textarea {
  display: block;
  width: 100%;
  padding: 0 20px;
  margin-bottom: 10px;
  background: #E9EFF6;
  line-height: 40px;
  border-width: 0;
  border-radius: 20px;
  font-family: 'Roboto', sans-serif;
}
.form-inner input[type="submit"] {
  margin-top: 30px;
  background: #f69a73;
  border-bottom: 4px solid #d87d56;
  color: white;
  font-size: 14px;
}
.form-inner textarea {resize: none;}
.text {
  margin-top: 0;
  font-family: 'Roboto', sans-serif;
  font-weight: 300;
  font-size: 20px;
  color: black;
  text-align: left;
  position: relative;
}
.checkbox {
  position: absolute;
  left: 230px;
  top: 333px;
}
</style>
