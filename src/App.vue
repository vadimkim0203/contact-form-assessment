<template>
  <div class="header-form-container">
    <h1>Связаться с нами</h1>
    <div class="form-image-container">
      <div class="form-container">
        <form @submit.prevent="submitForm">
          <div>
            <input type="name" placeholder="Имя" name="name" v-model="name" required />
          </div>
          <div class="input-wrapper">
            <div class="required-input-wrapper">
            <input class="required-input" type="phone" placeholder="Номер телефона" name="phone" v-model="phone"
              required /></div>
              <span class="required-star required-star-phone">*</span>
          </div>
          <div class="input-wrapper">
            <input class="required-input" type="email" placeholder="Email" name="email" v-model="email" required />
            <span class="required-star required-star-email">*</span>
          </div>
          <div>
            <input type="text" placeholder="Интересующий товар/услуга" name="subject" v-model="subject" required />
          </div>

          <div class="input-wrapper">
            <textarea class="required-input" name="message" rows="6" placeholder="Сообщение" v-model="message" required></textarea>
            <span class="required-star required-star-message">*</span>
          </div>

          <p class="privacy-policy">Отправляя заявку Вы соглашаетесь с политикой конфиденциальности</p>
          <button class="submit-button" type="submit">Отправить <i class="fas fa-arrow-right"></i></button>
        </form>
      </div>
      <div class="image-container"><img class="man-image" src="./assets/onthephone.png"
          alt="The man is talking on the phone"></div>
    </div>
  </div>
</template>

<style scoped>

.required-input-wrapper {
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

.submit-button {
  background-color: #333333;
  width: 222px;
  height: 71px;
  color: white;
  padding: 24px 47px;
  font-size: 12px;
  font-weight: 400;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  text-align: center;

  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
}

.submit-button:hover {
  background-color: #666666;
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