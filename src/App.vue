<template>
  <div class="header-container">
    <h1>Связаться с нами</h1>
  </div>
  <div class="form-image-container">
    <form @submit.prevent="submitForm">

      <div class="input-container">
        <input type="name" placeholder="Имя" name="name" v-model="name" required />
      </div>
      <div class="input-container">
        <input class="required-input" type="phone" placeholder="Номер телефона" name="phone" v-model="phone" required />
        <span class="required-asterisk required-asterisk-phone">*</span>
      </div>
      <div class="input-container">
        <input class="required-input" type="email" placeholder="E-mail" name="email" v-model="email" required />
        <span class="required-asterisk required-asterisk-email">*</span>
      </div>

      <div class="input-container"><input type="text" placeholder="Интересующий товар/услуга" name="subject"
          v-model="subject" required /></div>
      <div class="input-container">
        <textarea class="required-input" name="message" rows="4" placeholder="Сообщение" v-model="message"
          required></textarea>
        <span class="required-asterisk required-asterisk-message">*</span>
        <div class="check-container"><img class="check-logo"
            src="/Users/vadimkim/Desktop/contact-form-assessment/contact-form-assessment/src/assets/check.png" /></div>
      </div>


    </form>
    <div class="image-container"><img src="./assets/onthephone.png" alt="The man is talking on the phone"></div>
  </div>
  <div class="privacy-policy-container">
    <p class="privacy-policy">Отправляя заявку Вы соглашаетесь с политикой конфиденциальности</p>
  </div>
  <button class="submit-button" type="submit">
    ОТПРАВИТЬ
    <div class="arrow-container"><img
        src="/Users/vadimkim/Desktop/contact-form-assessment/contact-form-assessment/src/assets/arrow-2-right-long.png" />
    </div>
  </button>

</template>

<style scoped>
.header-container {
  margin-top: 0;
}

.form-image-container {
  display: flex;
  flex-direction: row;
  width: 1170px;
  height: 369px;
  gap: 30px;
  padding-right: 0px;
  margin-bottom: 20px;
}

.image-container {
  width: 749px;
  height: 369px;
  overflow: hidden;
}

.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.privacy-policy-container {
  font-weight: 400;
  font-size: 14px;
  width: 331px;
  height: 34px;
  margin-left: 40px;
  margin-bottom: 21px;

}

.submit-button {
  font-family: "TT Hoves", sans-serif;
  font-size: 12px;
  font-weight: 400;
  background-color: #333333;
  width: 221.81px;
  height: 71px;
  color: white;
  padding: 24px 47px;
  border: none;
  cursor: pointer;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
  position: absolute;
  bottom: -9px;
  left: 0px;
  letter-spacing: 0.2em;
}

.arrow-container {
  width: 24px;
  height: 24px;
}

.input-container {
  position: relative;
  display: inline-flex;
  align-items: center;

}

.required-asterisk {
  color: red;
  font-size: 1rem;
  /* Adjust size as needed */
  position: absolute;
}

.required-asterisk-phone {
  left: 138px;
}

.required-asterisk-email {
  left: 64px;
}

.required-asterisk-message {
  top: 12px;
  left: 99px;
}

.check-container {
  position: absolute;
  left: 6px;
}
</style>

<script>
export default {
  data() {
    return {
      name: "",
      phone: "",
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