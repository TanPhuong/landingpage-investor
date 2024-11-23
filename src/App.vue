<script>
import HomeView from './views/HomeView.vue';
import NavigationMobile from './components/NavigationMobile.vue';

export default {
  components: {
    HomeView,
    NavigationMobile,
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
      <nav class="navbar navbar-expand-lg w-100 p-0" v-if="!mobileView">
        <div class="container-fluid p-0">
          <a class="navbar-brand" href="#" style="width: 10%;">
            <img src="./assets/images/logo-transparent-2.png" alt="Logo" class="block w-100">
          </a>

          <div class="collapse navbar-collapse justify-content-end" id="navbarNav">
            <ul class="navbar-nav">
              <li class="nav-item me-4">
                <a class="nav-link aver-semi-bold" aria-current="page" href="#reason_section">Lý do nên đầu tư vào
                  Vietnam Tourist</a>
              </li>
              <li class="nav-item me-4">
                <a class="nav-link aver-semi-bold" href="#consultant_section">Về chúng tôi</a>
              </li>
              <li class="nav-item me-4">
                <a class="nav-link aver-semi-bold" href="#benefit_section">Ưu điểm khi chọn đầu tư</a>
              </li>
              <li class="nav-item me-4">
                <a class="nav-link aver-semi-bold" href="#privilege_section">Đặc quyền cao cấp dành riêng</a>
              </li>
            </ul>
          </div>

          <div class="btn-container">
            <button class="page-btn" data-bs-toggle="modal" data-bs-target="#staticBackdrop">Đăng ký tư vấn</button>
          </div>

        </div>
      </nav>

      <NavigationMobile v-if="mobileView"/>
    </header>

    <!-- Body part -->
    <HomeView :mobileView="mobileView"/>

    <footer class="position-relative">

      <!-- Returning top container -->
      <div class="return-top_container d-flex flex-column align-items-center" @click="backToTop">
        <svg width="25%%" height="18%%" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <g>
            <path fill="#3f3f3f"
              d="M26.0002 15.6569V40H22.0002V15.6569L11.2723 26.3848L8.44385 23.5564L24.0002 8L39.5566 23.5564L36.7282 26.3848L26.0002 15.6569Z" />
          </g>
        </svg>
        <div class="aver-semi-bold">Đầu trang</div>
      </div>

      <!-- Footer detail -->
      <div class="contact_container p-120 m-side-100">
        <div class="d-flex">
          <div class="firm_container">
            <div class="title aver-bold fs-4">Điều khoản</div>
            <div class="firm-items_container">
              <div class="firm-item mb-2">Nội quy</div>
              <div class="firm-item">Chính sách bảo mật</div>
            </div>

          </div>

          <div class="contact_wrapper">
            <div class="title aver-bold fs-4">Kết nối</div>

            <div class="contact-items_container">
              <div class="contact-item media_container d-flex mb-3">
                <div class="media-item">
                  <svg width="32" height="32" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path
                      d="M30.8048 42V28.0688H35.4694L36.1676 22.653H30.8048V19.1953C30.8048 17.6273 31.24 16.5587 33.4886 16.5587L36.3566 16.5573V11.7135C35.8604 11.6476 34.1582 11.5001 32.1776 11.5001C28.0426 11.5001 25.212 14.024 25.212 18.659V22.653H20.5354V28.0688H25.212V42H8C6.89544 42 6 41.1046 6 40V8C6 6.89544 6.89544 6 8 6H40C41.1046 6 42 6.89544 42 8V40C42 41.1046 41.1046 42 40 42H30.8048Z"
                      fill="black" />
                  </svg>
                </div>

                <div class="media-item mx-3">
                  <svg width="32" height="32" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path
                      d="M24.002 4C35.269 4 44.002 12.253 44.002 23.4C44.002 34.547 35.269 42.8 24.002 42.8C22.0466 42.8046 20.0994 42.546 18.213 42.031C17.8581 41.9336 17.4806 41.9616 17.144 42.11L13.175 43.862C12.688 44.0772 12.1258 44.036 11.6754 43.7522C11.2249 43.4684 10.9451 42.9792 10.929 42.447L10.82 38.889C10.8051 38.4514 10.6109 38.0392 10.283 37.749C6.39196 34.269 4.00196 29.231 4.00196 23.4C4.00196 12.253 12.735 4 24.002 4ZM11.992 29.073C11.428 29.968 12.528 30.976 13.37 30.337L19.681 25.547C20.1086 25.2244 20.6982 25.2244 21.126 25.547L25.799 29.047C26.4692 29.5498 27.3192 29.7494 28.1432 29.5974C28.9672 29.4454 29.6902 28.9558 30.137 28.247L36.012 18.927C36.576 18.032 35.476 17.024 34.634 17.663L28.323 22.453C27.8952 22.7756 27.3056 22.7756 26.878 22.453L22.205 18.953C21.5346 18.4502 20.6846 18.2506 19.8607 18.4026C19.0367 18.5546 18.3138 19.0442 17.867 19.753L11.992 29.073Z"
                      fill="black" />
                  </svg>
                </div>

                <div class="media-item">
                  <svg width="32" height="32" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path
                      d="M24.4878 8C25.556 8.00588 28.2286 8.03172 31.0682 8.14546L32.075 8.18936C34.934 8.32472 37.7906 8.55596 39.2074 8.951C41.0972 9.4819 42.5826 11.031 43.0846 12.9946C43.884 16.1128 43.984 22.1988 43.9964 23.6716L43.9982 23.9768V23.9982C43.9982 23.9982 43.9982 24.0056 43.9982 24.0198L43.9964 24.325C43.984 25.7978 43.884 31.8838 43.0846 35.002C42.5756 36.9728 41.0902 38.522 39.2074 39.0456C37.7906 39.4406 34.934 39.6718 32.075 39.8072L31.0682 39.851C28.2286 39.9648 25.556 39.9906 24.4878 39.9966L24.019 39.9982H23.9982C23.9982 39.9982 23.9912 39.9982 23.9774 39.9982L23.509 39.9966C21.2482 39.9842 11.7954 39.882 8.78902 39.0456C6.8992 38.5146 5.41384 36.9656 4.91174 35.002C4.1124 31.8838 4.01248 25.7978 4 24.325V23.6716C4.01248 22.1988 4.1124 16.1128 4.91174 12.9946C5.4208 11.0237 6.90616 9.47464 8.78902 8.951C11.7954 8.11446 21.2482 8.01244 23.509 8H24.4878ZM19.9982 16.9983V30.9982L31.9982 23.9982L19.9982 16.9983Z"
                      fill="black" />
                  </svg>
                </div>
              </div>

              <div class="contact-item company-address mb-2">
                Số 208, Hoàng Văn Thụ, Phường 4, Quận Tân Bình, TP. HCM
              </div>

              <div class="contact-item company-email page-text-blue mb-2">
                info@vietnamtouristvn.vn
              </div>

              <div class="contact-item company-phone page-text-blue mb-2">
                (028) 3636 0292 - (028) 3636 0293
              </div>
            </div>

          </div>
        </div>

        <hr style="color: #c6c6c6; margin: 72px 0;" v-if="!mobileView">
        <hr style="color: #c6c6c6; margin: 40px 0;" v-if="mobileView">

        <div class="fin_container d-flex align-items-center justify-content-evenly">
          <div class="img-wrapper">
            <img src="./assets/images/logo-transparent-2.png" alt="Logo" class="block w-100">
          </div>

          <div class="company-information">
            <div class="company-title text-uppercase fs-4 aver-bold page-text-gradient">Công ty CP Thương mại và dịch vụ
              du lịch Vietnam Tourist</div>
            <div class="information_container d-flex mt-2">
              <div class="infor-item pe-3">
                <svg width="16px" height="16px" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path
                    d="M24 4C35.0456 4 44 12.9543 44 24C44 35.0456 35.0456 44 24 44C12.9543 44 4 35.0456 4 24C4 12.9543 12.9543 4 24 4ZM32.0086 25.7554C31.3178 24.7066 30.8194 23.9492 28.9244 24.2496C25.3434 24.818 24.9464 25.4448 24.7754 26.475L24.7272 26.7886L24.6786 27.1194C24.4832 28.4856 24.4906 29.0024 25.1178 29.6616C27.6482 32.3164 29.164 34.23 29.6232 35.3492C29.8474 35.8968 30.4238 37.5502 30.0272 39.1854C32.4744 38.2132 34.6312 36.6664 36.3306 34.7118C36.551 33.9642 36.7102 33.0332 36.7102 31.9036V31.6944C36.7102 29.8494 36.7102 29.008 35.4062 28.2628C34.856 27.9502 34.4454 27.762 34.1164 27.6128C33.382 27.2788 32.8958 27.0594 32.2396 26.0998C32.1614 25.9856 32.085 25.8716 32.0086 25.7554ZM24 7.66666C19.3652 7.66666 15.1812 9.59716 12.2084 12.6979C12.5623 12.9437 12.8707 13.2891 13.0826 13.7651C13.4906 14.6806 13.4906 15.6224 13.4906 16.4553C13.4898 17.1124 13.4888 17.7344 13.6998 18.186C13.9889 18.8027 15.2328 19.0645 16.331 19.2947C16.7233 19.3773 17.1279 19.4617 17.4959 19.5635C18.5081 19.8447 19.2911 20.753 19.9188 21.4824C20.1792 21.7862 20.5638 22.2326 20.7566 22.3434C20.8572 22.2712 21.18 21.9216 21.3398 21.347C21.4614 20.9094 21.4268 20.5194 21.2478 20.3086C20.1296 18.9889 20.1904 16.4464 20.536 15.5099C21.0804 14.0321 22.781 14.1412 24.024 14.2219C24.4876 14.2518 24.9252 14.2805 25.2514 14.2395C26.4964 14.0833 26.8792 12.1908 27.15 11.82C27.7342 11.0196 29.5214 9.8142 30.6316 9.06908C28.605 8.16764 26.361 7.66666 24 7.66666Z"
                    fill="black" />
                </svg>
                vietnamtouristvn.com
              </div>

              <div class="infor-item px-3">
                Mã số thuế: 0314576147
              </div>

              <div class="infor-item ps-3">
                Số GP: 79-1459/2022/CDLQGVN-GP LHQT
              </div>
            </div>
          </div>
        </div>
      </div>
    </footer>

    <div class="copy-right text-center text-white">
      Copyright
      <svg xmlns="http://www.w3.org/2000/svg" width="16px" height="16px" viewBox="0 0 24 24">
        <path fill="#fff"
          d="M11.88 9.14c1.28.06 1.61 1.15 1.63 1.66h1.79c-.08-1.98-1.49-3.19-3.45-3.19C9.64 7.61 8 9 8 12.14c0 1.94.93 4.24 3.84 4.24c2.22 0 3.41-1.65 3.44-2.95h-1.79c-.03.59-.45 1.38-1.63 1.44c-1.31-.04-1.86-1.06-1.86-2.73c0-2.89 1.28-2.98 1.88-3M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10s10-4.48 10-10S17.52 2 12 2m0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8s8 3.59 8 8s-3.59 8-8 8" />
      </svg>
      2024 Vietnam Tourist
    </div>

  </main>
</template>

<style>
main {
  font-family: 'AvertaRegular', sans-serif;
  font-weight: normal;
}

input[type="number"]::-webkit-outer-spin-button,
input[type="number"]::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

.w-95 {
  width: 95%;
  margin: auto;
}

.page-text-blue {
  color: #005ea0 !important;
}

.page-text-gradient {
  background: linear-gradient(#0082df, #005ea0);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.page-text-gradient-pink {
  background: linear-gradient(#f0598c, #ef3b6d);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.page-gradient-blue {
  background: linear-gradient(#0082df, #005ea0);
}

.page-gradient-pink {
  background: linear-gradient(#f0598c, #ef3b6d);
}

.m-side-100 {
  margin: 0 100px;
}

.p-120 {
  padding: 120px 0;
}

header {
  height: 80px;
  padding: 0 40px;
  position: sticky;
  top: 0;
  right: 0;
  left: 0;
  box-shadow: 0 0 6px #cccbcb;
  z-index: 1;

  & nav {
    & .container-fluid {
      height: inherit;

      & .collapse {
        width: 65%;
      }

      & .navbar-nav {
        font-size: 14px;
      }
    }
  }

  & .navbar-brand {
    width: 15%;
    height: inherit;

    & img {
      max-height: 80px;
      max-width: 180px;
      object-fit: cover;
    }
  }
}


.nav-item:hover a {
  color: #005ea0 !important;
}

.page-btn {
  padding: 12px 24px;
  font-size: 16px;
  font-family: 'AvertaSemibold', sans-serif !important;
  background: linear-gradient(#f0578a, #f03d6f);
  color: #fff;
  border-radius: 15px;
  border: none;
}

.page-btn:hover {
  box-shadow: 0 0 8px #f05083;
}

footer {
  background-color: #f7f7f7;

  & .return-top_container {
    width: 91px;
    height: 125px;
    padding: 40px 12px;
    cursor: pointer;
    border-radius: 100px;
    color: #606060;
    background-color: #e6e6e6;
    position: absolute;
    top: -8%;
    right: 5%;

    & div {
      font-size: 14px;
      color: #3f3f3f;
    }
  }

  & .contact_container {
    padding-bottom: 72px;

    & .firm_container {
      margin-right: 100px;
    }

    & .firm-items_container,
    .contact-items_container {
      margin-top: 32px;
    }

    & .fin_container {

      & .img-wrapper {
        width: 20%;

        & img {
          max-width: 320px;
        }
      }

      & .company-information {

        & .infor-item:nth-child(2) {
          border-left: 1px solid #c6c6c6;
          border-right: 1px solid #c6c6c6;
        }
      }
    }
  }
}

.copy-right {
  padding: 12px 100px;
  background: radial-gradient(#0082df, #005ea0);
}

@media (max-width: 1024px) {

  header {
    height: 56px;
    padding: 8px 16px;
  }

  .page-btn {
    font-size: 12px !important;
    padding: 8px 16px;
    border-radius: 12px;
  }

  footer {
    & .return-top_container {
      width: 69px;
      height: 92px;
      padding: 28px 6px !important;
      top: -7%;

      & div {
        font-size: 12px;
        margin-top: 4px;
      }
    }

    & .contact_container {
      padding: 80px 0 40px;
      margin: 0 16px;

      & .firm_container {
        margin: 0;
        width: 50%;
        min-width: 131px;

        & .title {
          font-size: 18px !important;
        }

        & .firm-items_container {
          margin-top: 24px;

          & .firm-item {
            font-size: 14px;
          }
        }
      }

      & .contact_wrapper {
        margin-left: 24px;

        & .title {
          font-size: 18px !important;
        }

        & .contact-items_container {
          margin-top: 24px;

          & .contact-item {
            font-size: 14px;
          }
        }
      }

      & .fin_container {
        flex-direction: column;
        align-items: unset !important;

        & .img-wrapper {
          width: 50%;
        }

        & .company-information {

          & .company-title {
            font-size: 16px !important;
          }

          & .information_container {
            flex-wrap: wrap;

            & .infor-item {
              font-size: 14px;
            }
          }
        }
      }
    }

  }

  .copy-right {
    font-size: 12px;
    padding: 12px 90px;
  }

}
</style>
