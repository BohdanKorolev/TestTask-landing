<template>
  <div class="col-lg-6 col-md-8">
    <div class="form__attention">
      <p class="mockup-p text-center">
        Attention! After successful registration and alert, update the list of users in the block from the top
      </p>
    </div>
    <form class="form__fields" @input="formValidation">
      <div class="form-group form__form-group">
        <label for="name" class="mockup-p mockup-letter-spacing">Name</label>
        <input type="text"
               class="form-control"
               :class="{ 'is-invalid': !isNameOk }"
               id="name"
               @input="onNameInput($event)"
               placeholder="Your name">
        <div class="invalid-feedback">Error</div>
      </div>
      <div class="form-group form__form-group">
        <label for="email" class="mockup-p mockup-letter-spacing">Email</label>
        <input type="email"
               class="form-control"
               :class="{ 'is-invalid': !isEmailOk }"
               id="email"
               @input="onEmailInput($event)"
               placeholder="Your email">
        <div class="invalid-feedback">Error</div>
      </div>
      <div class="form-group form__form-group">
        <label for="phone" class="mockup-p mockup-letter-spacing">Phone number</label>
        <input type="text"
               class="form-control"
               :class="{ 'is-invalid': !isPhoneOk }"
               id="phone"
               @input="onPhoneInput($event)"
               aria-describedby="phoneHelp"
               placeholder="+380 XX XXX XX XX">
        <div class="invalid-feedback">Error</div>
        <small id="phoneHelp" class="form-text text-muted form__help-text">
          Enter phone number in open format
        </small>
      </div>
      <div class="form__radio-wrap">
        <label class="mockup-p mockup-letter-spacing">Select your position</label>
        <div class="form__radio">
          <div class="custom-control custom-radio form__radio-group" v-for="position of this.positions">
            <input type="radio"
                   name="position"
                   :id="position.id"
                   :value="position.id"
                   class="custom-control-input"
                   v-model="newUser.position_id">
            <label class="custom-control-label mockup-p mockup-letter-spacing"
                   :for="position.id">{{position.name}}</label>
          </div>
        </div>
      </div>
      <div class="form-group form__form-group">
        <label for="file" class="mockup-p mockup-letter-spacing">Photo</label>
        <div class="custom-file form-control">
          <input type="file"
                 class="custom-file-input form-control-file"
                 :class="{ 'is-invalid': !isFileOk }"
                 id="file"
                 @input="onFileChange($event)">
          <label class="custom-file-label form-control-file"
                 for="file">Upload your photo</label>
          <div class="invalid-feedback">Error</div>
        </div>
      </div>
      <div class="form__button text-center">
        <button class="btn btn-danger mockup-button"
                type="submit"
                @click.prevent="postUserData"
                :disabled="!isFormValid">Sing up now</button>
      </div>
    </form>
  </div>
</template>

<script>
  export default {
    name: "UserForm",
    data() {
      return {
        token: '',
        isNameOk: true,
        isEmailOk: true,
        isPhoneOk: true,
        isFileOk: true,
        isFormValid: false,
        positions: [],
        newUser: {
          name: '',
          phone: '',
          email: '',
          photo: {},
          position_id: 1,
        },
      };
    },
    methods: {
      // data sending methods
      getPositions() {
        fetch('https://frontend-test-assignment-api.abz.agency/api/v1/positions')
          .then(function(response) {
            return response.json();
          })
          .then((data) => {
            this.positions = data.positions;
          })
          .catch(function(error) {
            setTimeout(this.getPositions,5000)
          });
      },
      postUserData() {
        fetch('https://frontend-test-assignment-api.abz.agency/api/v1/token')
          .then(function(response) {
            return response.json();
          })
          .then((data) => {
            this.sendData(data.token);
          })
      },
      sendData(token) {
        fetch('https://frontend-test-assignment-api.abz.agency/api/v1/users', {
          method: 'POST',
          body: this.dataGeneration(),
          headers: {
            'Token': token,
          },
        })
          .then(function(response) {
            return response.json();
          })
          .then((data) => {
            if(data.success) {
              this.$emit('data-sanded', 'You have successfully passed the registration')
            } else {
              this.$emit('data-sanded', data.message)
            }
          })
      },
      // data generation to receive & clear fields method after complete
      dataGeneration() {
        let formData = new FormData();
        formData.append('position_id', this.newUser.position_id);
        formData.append('name', this.newUser.name);
        formData.append('email', this.newUser.email);
        formData.append('phone', this.newUser.phone);
        formData.append('photo', this.newUser.photo);
        return formData;
      },
      clearFields() {
        this.newUser.name = '';
        this.newUser.email = '';
        this.newUser.phone = '';
        this.newUser.photo = {};
      },
      // form 'validation' event
      formValidation() {
        this.isFormValid = (
          this.isNameOk &&
          this.isEmailOk &&
          this.isPhoneOk &&
          this.isFileOk &&
          this.newUser.name &&
          this.newUser.email &&
          this.newUser.phone &&
          (this.newUser.photo.type == 'image/jpeg')
        );
      },
      // fields events
      onNameInput(e) {
        if (this.isNameOk = e.target.value != '') {
          this.newUser.name = e.target.value;
        } else {
          this.isNameOk = false;
        }
      },
      onEmailInput(e) {
        if (this.isEmailOk = (/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(e.target.value))) {
          this.newUser.email = e.target.value;
        } else {
          this.isEmailOk = false;
        }
      },
      onPhoneInput(e) {
        if (this.isPhoneOk = (/^\+380\d{9}$/.test(e.target.value))) {
          this.newUser.phone = e.target.value;
        } else {
          this.isPhoneOk = false
        }
      },
      onFileChange(e) {
        let files = e.target.files || e.dataTransfer.files;
        if (!files.length){
          return;
        } else if ((/^.*\.(jpg|JPG|jpeg|JPEG)$/.test(files[0].name) &&
          (files[0].size < 5000000))) {
          this.newUser.photo = files[0];
          this.isFileOk = true
        } else {
          this.isFileOk = false;
        }
      },
    },
    created() {
      this.getPositions();
    }
  }
</script>

<style lang="scss" scoped>
  .form {
    &__attention {
      margin-top: 1.6em;
    }
    &__fields {
      margin-top: 2.7em;
    }
    &__form-group {
      margin-bottom: 2.1em;
    }
    &__help-text {
      font-size: 12px;
    }
    &__radio {
      margin: 0.5em 0;;
    }
    &__radio-group {
      margin-bottom: 0.6em;
    }
    &__radio-wrap {
      margin-bottom: 1.6em;
    }
    &__button {
      margin-top: 3.2em;
      margin-bottom: 1.3em;
      @media only screen and (max-width: 1024px) {
        margin-bottom: .3em;
      }
    }
  }
</style>
