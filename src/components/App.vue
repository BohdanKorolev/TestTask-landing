<template>
  <div>
    <div class="container-fluid mockup-container px-0">
      <nav class="navbar navigation navbar-expand-lg navbar-light sticky-top">
        <a class="navigation__brand" href="#">
          <img src="/assets/img/logo.svg" alt="">
        </a>
        <button class="navbar-toggler navigation__toggler" type="button" data-toggle="collapse" data-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
          <img src="/assets/img/menu icon.svg" @click="asideToggle" alt="">
        </button>
        <div class="collapse navbar-collapse" id="navbarText">
          <ul class="navbar-nav ml-auto">
            <li class="nav-item active">
              <a class=" navigation__link" href="#">About me <span class="sr-only">(current)</span></a>
            </li>
            <li class="nav-item">
              <a class=" navigation__link" href="#">Relationships</a>
            </li>
            <li class="nav-item">
                <a class=" navigation__link" href="#">Requirements</a>
            </li>
            <li class="nav-item">
              <a class="navigation__link" href="#users">Users</a>
            </li>
            <li class="nav-item">
              <a class="navigation__link" href="#name">Sign Up</a>
            </li>
          </ul>
        </div>
      </nav>
    </div>
    <div v-show="aside" class="aside" @click.stop="asideToggle">
      <aside class="aside__wrap mockup-bg">
        <div class="aside__brand">
          <img src="/assets/img/logo.svg" alt="">
        </div>
        <ul class="aside__section nav flex-column">
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#">About me</a>
          </li>
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#">Relationship</a>
          </li>
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#">Users</a>
          </li>
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#name">Sign Up</a>
          </li>
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#">Terms and Conditions</a>
          </li>
        </ul>
        <ul class="aside__section nav flex-column">
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#">How it works</a>
          </li>
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#">Partnership</a>
          </li>
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#">Help</a>
          </li>
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#">Leave testimonial</a>
          </li>
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#">Contact us</a>
          </li>
        </ul>
        <ul class="aside__section nav flex-column">
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#">Articles</a>
          </li>
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#">Our news</a>
          </li>
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#">Testimonials</a>
          </li>
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#">Licenses</a>
          </li>
          <li class="nav-item">
            <a class="nav-link aside__nav-link mockup-p" href="#">Privacy Policy</a>
          </li>
        </ul>
      </aside>
    </div>
    <main>
      <header class="header container-xl mockup-container">
        <div class="row mx-md-0 header__content">
          <div class="col-lg-7 col-md-8">
            <div class="header__title mr-lg-4 mr-md-5">
              <h1 class="mockup-heading mockup-letter-spacing m-0">Test assignment for Frontend Developer position</h1>
            </div>
            <div class="header__text header__text-lg mr-lg-3 mr-md-2">
              <p class="mockup-p mb-0">
                We kindly remind you that your test assignment should be submitted as a link to github/bitbucket repository.
                Please be patient, we consider and respond to every application that meets minimum requirements.
                We look forward to your submission. Good luck! The photo has to scale in the banner area on the different screens
              </p>
            </div>
            <div class="header__text header__text-mobile">
              <p class="mockup-p mb-0">
                We kindly remind you that your test assignment should be submitted as a link to github/bitbucket repository.
              </p>
            </div>
            <div class="header__button">
              <a href="#name">
                <button class="btn btn-danger mockup-button">Sing up now</button>
              </a>
            </div>
          </div>
        </div>
      </header>
      <section class="section section__content container-xl mockup-container">
        <header class="section__title">
          <h2 class="mockup-heading mockup-letter-spacing m-0 text-center">
            Let's get acquainted
          </h2>
        </header>
        <div class="row mx-0 section__row">
          <div class="col-lg-5 col-md-5">
            <div class="section__img">
              <img srcset="/assets/img/man-laptop-360.jpg 289w,
                         /assets/img/man-laptop-768.jpg 247w,
                         /assets/img/man-laptop-1024.jpg 339w"
                   sizes="(max-width: 767px) 289px,
                        (max-width: 1023px) 247px,
                        339px"
                   alt="">
            </div>
          </div>
          <div class="col-lg-7 col-md-7 pl-md-0 ml-md-n3 ml-lg-0 pl-lg-3 section__text-block">
            <div class="section__text">
              <h2 class="mockup-heading2 m-0">
                I am cool frontend developer
              </h2>
            </div>
            <div class="section__text">
              <p class="mockup-p mb-0 text-justify">
                We will evaluate how clean your approach to writing CSS and Javascript code is. You can use any CSS and Javascript 3rd party libraries without any restriction.
              </p>
            </div>
            <div class="section__text">
              <p class="mockup-p mb-0 text-justify">
                If 3rd party css/javascript libraries are added to the project via bower/npm/yarn you will get bonus points. If you use any task runner (gulp/webpack) you will get bonus points as well. Slice service directory page P​SD mockup​ into HTML5/CSS3.
              </p>
            </div>
            <div class="section__button">
              <a href="#name">
                <button type="button" class="btn mockup-button-light btn-link">Sing up now</button>
              </a>
            </div>
          </div>
        </div>
      </section>
      <section class="section section__content mockup-bg2 container-xl mockup-container" id="users">
        <header class="section__title text-center">
          <h2 class="mockup-heading mockup-letter-spacing m-0 text-center">
            Our cheerful users
          </h2>
          <p class="mockup-p mb-0 section__text-attention">
            Attention! Sorting users by registration date
          </p>
        </header>
        <div class="row mx-3 section__row">
          <div class="col-md-4 user" v-for="user of users">
            <app-user :key="user.id"
                      :data="user"
            ></app-user>
          </div>
          <div class="section__button text-center col-12">
            <button type="button"
                    class="btn btn-danger mockup-button"
                    @click="getUsersData"
                    :disabled="allUsersUploaded">Show more</button>
          </div>
        </div>
      </section>
      <section class="section section__content mockup-bg container-xl mockup-container" id="registerForm">
        <header class="section__title text-center">
          <h2 class="mockup-heading m-0 text-center">
            Register to get a work
          </h2>
        </header>
        <div class="row mx-3 justify-content-center form">
          <app-user-form
            @data-sanded="dataSanded($event)"
          ></app-user-form>
        </div>
      </section>
      <footer class="row mx-0 footer justify-content-center">
        <p class="footer__text mockup-p">
          © bohdan.korolev specially for the test task
        </p>
      </footer>
    </main>
    <app-modal v-if="showModal"
               @close="showModal = false"
               :message="message"></app-modal>
  </div>
</template>

<script>
  import User from './User.vue';
  import UserForm from './UserForm.vue';
  import Modal from './Modal.vue';

  export default {
    components: {
      appUser: User,
      appUserForm: UserForm,
      appModal: Modal,
    },
    data () {
      return {
        aside: false,
        showModal: false,
        message: '',
        users: [],
        totalUsers: 0,
        allUsersUploaded: false,
        link: 'https://frontend-test-assignment-api.abz.agency/api/v1/users?page=1&count=6',
      };
    },
    methods: {
      // get all data from the server when App created
      getUsersData() {
        fetch(this.link)
          .then(function(response) {
            return response.json();
          })
          .then((data) => {
            this.link = data.links['next_url'];
            this.totalUsers = data['total_users'];
            data.users.forEach(user => this.users.push(user));
            this.users.sort((a, b) => a['registration_timestamp'] > b['registration_timestamp'] ? -1 : 1);
            if (this.users.length === this.totalUsers) {
              this.allUsersUploaded = true;
            }
          })
      },
      updateUsersData() {
        fetch('https://frontend-test-assignment-api.abz.agency/api/v1/users?page=1&count=6')
          .then(function(response) {
            return response.json();
          })
          .then((data) => {
            this.users = [];
            data.users.forEach(user => this.users.push(user));
            this.users.sort((a, b) => a['registration_timestamp'] > b['registration_timestamp'] ? -1 : 1);
          })
      },
      // aside toggle method
      asideToggle() {
        if (this.aside) {
          document.body.style.overflowY = 'auto';
        } else {
          document.body.style.overflowY = 'hidden';
        }
        this.aside = !this.aside;
      },
      // event after form complete
      dataSanded(e) {
        this.showModal = true;
        this.message = e;
        this.updateUsersData();
      },
    },
    created() {
      this.getUsersData();
    }
  };
</script>

<style lang="scss" scoped>

</style>
