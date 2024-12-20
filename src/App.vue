<template>
  <h1>Связаться с нами</h1>
  <div class="form-image-container">
    <form @submit.prevent="submitForm">

      <div class="input-container">
        <input type="name" placeholder="Имя" name="name" v-model="name" required />
      </div>



      <input class="required-input" type="phone" placeholder="Номер телефона*" name="phone" v-model="phone" required />



      <input class="required-input" type="email" placeholder="E-mail*" name="email" v-model="email" required/>


      <input type="text" placeholder="Интересующий товар/услуга" name="subject" v-model="subject" required />



      <textarea class="required-input" name="message" rows="6" placeholder="Сообщение*" v-model="message"
        required></textarea>

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
.form-image-container {
  display: flex;
  flex-direction: row;
  width: 1170px;
  height: 369px;
  gap: 30px;
  padding-right: 0px;
}

.image-container {
  width: 749px;
  height: 369px;
  overflow: hidden;
}

.privacy-policy-container {
  width: 331px;
  height: 34px;
  margin-left: 40px;
  margin-top: 22px;
}

.submit-button {
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
  bottom: 0px;
  left: 0px;
}

.arrow-container {
  width: 24px;
  height: 24px;
}


/* .required-input-wrapper {
  position:relative
}

.required-star {
  position:absolute;
  color: red;
}

.required-star-phone {
  left: 183px;
  top: 195px;
}

.required-star-email {
  left: 97px;
  top: 259px; 
}

.required-star-message {
  left: 141px;
  top: 387px; 
}


.form-image-container {
  display: flex;
  flex-direction: row;
  gap: 30px;
  width: 100vw;
}

.man-image {
  max-width: 749px;
}


.privacy-policy {
  color: red;
}



.submit-button:hover {
  background-color: #666666;
} */
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