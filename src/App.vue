<script>
import HomeView from './views/HomeView.vue';
import NavigationMobile from './components/NavigationMobile.vue';

export default {
  components: {
    HomeView,
    NavigationMobile
  },
  data: () => {
    return {
      mobileView: false
    }
  },
  methods: {
    handleView() {
      if (window.innerWidth <= 1024) {
        this.mobileView = true;
      } else {
        this.mobileView = false;
      }
    },
    backToTop() {
      window.scrollTo({
        top: 0,
        behavior: 'smooth'
      })
    }
  },
  created() {
    this.handleView();
  }
}

</script>

<template>
  <main>
    <header class="w-100 bg-light">
      <nav class="navbar navbar-expand-lg w-95" v-if="!mobileView">
        <div class="container-fluid p-0">
          <a class="navbar-brand" href="#" style="width: 35%;">
            <img src="./assets/images/logo-transparent-2.png" alt="Logo" class="block" style="width: 30%;">
          </a>

          <div class="collapse navbar-collapse justify-content-end" id="navbarNav" style="width: 65%;">
            <ul class="navbar-nav">
              <li class="nav-item me-4">
                <a class="nav-link aver-extra-bold" aria-current="page" href="#reason_section">Lý do nên đầu tư vào Vietnam
                  Tourist</a>
              </li>
              <li class="nav-item me-4">
                <a class="nav-link aver-extra-bold" href="#consultant_section">Về chúng tôi</a>
              </li>
              <li class="nav-item me-4">
                <a class="nav-link aver-extra-bold" href="#benefit_section">Ưu điểm khi chọn đầu tư</a>
              </li>
              <li class="nav-item me-4">
                <a class="nav-link aver-extra-bold" href="#privilege_section">Đặc quyền cao cấp dành riêng</a>
              </li>
            </ul>
          </div>

          <div class="btn-container" style="width: 10%;">
            <button class="page-btn">Đăng ký tư vấn</button>
          </div>

        </div>
      </nav>

      <NavigationMobile v-if="mobileView" />
    </header>

    <!-- Body part -->
    <HomeView :mobileView="mobileView" />

    <footer style="background-color: #f7f7f7; position: relative;" >

      <div class="return-top_container d-flex flex-column justify-content-center align-items-center" @click="backToTop">
        <svg width="30%" height="30%" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <g opacity="0.7">
            <path fill="#606060"
              d="M26.0002 15.6569V40H22.0002V15.6569L11.2723 26.3848L8.44385 23.5564L24.0002 8L39.5566 23.5564L36.7282 26.3848L26.0002 15.6569Z" />
          </g>
        </svg>
        <div class="text" style="font-size: 14px;">Đầu trang</div>
      </div>

      <div class="p-70" style="width: 85%; margin: auto;">
        <div class="contact_container d-flex" style="padding-bottom: 50px;">
          <div class="firm_container">

            <div class="title aver-bold fs-5">Điều khoản</div>
            <div class="firm-items_container mt-4">
              <div class="firm-item mb-2">Nội quy</div>
              <div class="firm-item">Chính sách bảo mật</div>
            </div>

          </div>

          <div class="contact_container ms-5">
            <div class="title aver-bold fs-5">Kết nối</div>

            <div class="contact-items_container mt-4">
              <div class="contact-item media_container d-flex mb-2">
                <div class="media-item">
                  <svg xmlns="http://www.w3.org/2000/svg" width="30px" height="30px" viewBox="0 0 24 24">
                    <path fill="currentColor"
                      d="M20.9 2H3.1A1.1 1.1 0 0 0 2 3.1v17.8A1.1 1.1 0 0 0 3.1 22h9.58v-7.75h-2.6v-3h2.6V9a3.64 3.64 0 0 1 3.88-4a20 20 0 0 1 2.33.12v2.7H17.3c-1.26 0-1.5.6-1.5 1.47v1.93h3l-.39 3H15.8V22h5.1a1.1 1.1 0 0 0 1.1-1.1V3.1A1.1 1.1 0 0 0 20.9 2" />
                  </svg>
                </div>

                <div class="media-item mx-3">
                  <svg xmlns="http://www.w3.org/2000/svg" width="30px" height="30px" viewBox="0 0 24 24">
                    <path fill="currentColor"
                      d="M12 2C6.36 2 2 6.13 2 11.7c0 2.91 1.19 5.44 3.14 7.17c.16.13.26.35.27.57l.05 1.78c.04.57.61.94 1.13.71l1.98-.87c.17-.06.36-.09.53-.06c.9.27 1.9.4 2.9.4c5.64 0 10-4.13 10-9.7S17.64 2 12 2m6 7.46l-2.93 4.67c-.47.73-1.47.92-2.17.37l-2.34-1.73a.6.6 0 0 0-.72 0l-3.16 2.4c-.42.33-.97-.17-.68-.63l2.93-4.67c.47-.73 1.47-.92 2.17-.4l2.34 1.76a.6.6 0 0 0 .72 0l3.16-2.4c.42-.33.97.17.68.63" />
                  </svg>
                </div>

                <div class="media-item">
                  <svg xmlns="http://www.w3.org/2000/svg" width="30px" height="30px" viewBox="0 0 24 24">
                    <path fill="currentColor"
                      d="M12.244 4c.534.003 1.87.016 3.29.073l.504.022c1.429.067 2.857.183 3.566.38c.945.266 1.687 1.04 1.938 2.022c.4 1.56.45 4.602.456 5.339l.001.152v.174c-.007.737-.057 3.78-.457 5.339c-.254.985-.997 1.76-1.938 2.022c-.709.197-2.137.313-3.566.38l-.504.023c-1.42.056-2.756.07-3.29.072l-.235.001h-.255c-1.13-.007-5.856-.058-7.36-.476c-.944-.266-1.687-1.04-1.938-2.022c-.4-1.56-.45-4.602-.456-5.339v-.326c.006-.737.056-3.78.456-5.339c.254-.985.997-1.76 1.939-2.021c1.503-.419 6.23-.47 7.36-.476zM9.999 8.5v7l6-3.5z" />
                  </svg>
                </div>
              </div>

              <div class="contact-item company-address mb-2">
                Số 208, Hoàng Văn Thụ, Phường 4, Quận Tân Bình, TP. HCM
              </div>

              <div class="contact-item company-email mb-2" style="color: #005ea0;">
                info@vietnamtouristvn.vn
              </div>

              <div class="contact-item company-phone mb-2" style="color: #005ea0;">
                (028) 3636 0292 - (028) 3636 0293
              </div>
            </div>

          </div>
        </div>

        <hr style="color: #c6c6c6;">

        <div class="fin_container d-flex align-items-center" style="padding-top: 50px;">
          <div class="img-wrapper" style="width: 40%;">
            <img src="./assets/images/logo-transparent-2.png" alt="Logo" class="block w-50">
          </div>

          <div class="company-information">
            <div class="company-title text-uppercase fs-3 aver-bold page-text-gradient">Công ty CP Thương mại và
              dịch vụ du lịch Vietnam Tourist</div>
            <div class="information_container d-flex mt-2">
              <div class="infor-item pe-3">
                <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24">
                  <path fill="currentColor"
                    d="M17.9 17.39c-.26-.8-1.01-1.39-1.9-1.39h-1v-3a1 1 0 0 0-1-1H8v-2h2a1 1 0 0 0 1-1V7h2a2 2 0 0 0 2-2v-.41a7.984 7.984 0 0 1 2.9 12.8M11 19.93c-3.95-.49-7-3.85-7-7.93c0-.62.08-1.22.21-1.79L9 15v1a2 2 0 0 0 2 2m1-16A10 10 0 0 0 2 12a10 10 0 0 0 10 10a10 10 0 0 0 10-10A10 10 0 0 0 12 2" />
                </svg>
                vietnamtouristvn.com
              </div>

              <div class="infor-item px-3" style="border-left: 1px solid #c6c6c6; border-right: 1px solid #c6c6c6;">
                Mã số thuế: 0314576147
              </div>

              <div class="infor-item ps-3">
                Số GP: 79-1459/2022/CDLQGVN-GP LHQT
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="copy-right page-gradient-blue text-center py-2 text-white">
        Copyright
        <svg xmlns="http://www.w3.org/2000/svg" width="16px" height="16px" viewBox="0 0 24 24">
          <path fill="#fff"
            d="M11.88 9.14c1.28.06 1.61 1.15 1.63 1.66h1.79c-.08-1.98-1.49-3.19-3.45-3.19C9.64 7.61 8 9 8 12.14c0 1.94.93 4.24 3.84 4.24c2.22 0 3.41-1.65 3.44-2.95h-1.79c-.03.59-.45 1.38-1.63 1.44c-1.31-.04-1.86-1.06-1.86-2.73c0-2.89 1.28-2.98 1.88-3M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10s10-4.48 10-10S17.52 2 12 2m0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8s8 3.59 8 8s-3.59 8-8 8" />
        </svg>
        2024 Vietnam Tourist
      </div>
    </footer>

  </main>
</template>

<style>
main {
  font-family: 'AvertaRegular', sans-serif;
}

.w-95 {
  width: 95%;
  margin: auto;
}

.page-text-gradient {
  background: linear-gradient(to right, #0181de, #0160a2);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.page-gradient-blue {
  background: linear-gradient(#0181de, #0160a2);
}

.page-gradient-pink {
  background: linear-gradient(#f0578a, #f03d6f);
}

.m-70 {
  margin: 70px auto;
}

.p-70 {
  padding: 70px 0;
}

header {
  position: sticky;
  top: 0;
  right: 0;
  left: 0;
  box-shadow: 0 0 6px #cccbcb;
  z-index: 1;
}

.nav-item:hover a {
  color: #005ea0 !important;
}

.page-btn {
  padding: 12px 25px;
  background: linear-gradient(#f0578a, #f03d6f);
  color: #fff;
  border-radius: 15px;
  border: none;
}

.page-btn:hover {
  box-shadow: 0 0 8px #f05083;
}

.return-top_container {
  width: 90px;
  height: 110px;
  cursor: pointer;
  border-radius: 40%;
  color: #606060;
  background-color: #e6e6e6; 
  position: absolute;
  top: -8%;
  right: 5%;
}

@media (max-width: 1024px) {

  footer .fin_container {
    display: block !important;

    & .img-wrapper {
      width: 60% !important;

      & img {
        width: 100% !important;
      }
    }

    & .company-information {
      margin-top: 20px;

      & .information_container {
        flex-wrap: wrap;

        & .infor-item {
          border: none !important;
          margin-bottom: 10px;
        }
      }
    }
  }

  .return-top_container {
    width: 80px;
    height: 100px;
    font-size: 12px;
    top: -5%;
  }
}
</style>
