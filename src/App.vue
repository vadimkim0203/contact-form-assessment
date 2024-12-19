<template>
  <h1>Связаться с нами</h1>
  <form @submit.prevent="submitForm">
    <div>
      <input
        type="name"
        placeholder="Имя"
        name="name"
        v-model="name"
        required
      />
    </div>
    <div>
      <input
        type="phone"
        placeholder="Номер телефона"
        name="phone"
        v-model="phone"
        required
      />
    </div>
    <div>
      <input
        type="email"
        placeholder="Email"
        name="email"
        v-model="email"
        required
      />
    </div>
    <div>
      <input
        type="text"
        placeholder="Интересующий товар/услуга"
        name="subject"
        v-model="subject"
        required
      />
    </div>

    <div>
      <textarea
        name="message"
        rows="6"
        placeholder="Сообщение"
        v-model="message"
        required
      ></textarea>
    </div>

    <p>Отправляя заявку Вы соглашаетесь с политикой конфиденциальности</p>

    <button type="submit">Отправить</button>
  </form>
</template>

<script>
  export default {
    data() {
      return {
        name:"",
        phone:"",
        email: "",
        subject: "",
        message: "",
      };
    },
    methods: {
      async submitForm() {
        const response = await fetch("https://formbold.com/s/unique_form_id", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            Accept: "application/json",
          },
          body: JSON.stringify({
            name: this.email,
            phone: this.phone,
            email: this.email,
            subject: this.subject,
            message: this.message,
          }),
        });
        const result = await response.json();
        if (response.ok) {
          alert(result.message);
          this.$el.reset();
        } else {
          alert(response.message || "Something went wrong");
        }
      },
    },
  };
</script>