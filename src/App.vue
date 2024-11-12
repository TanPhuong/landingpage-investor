<script setup>
import HomeView from './views/HomeView.vue';
</script>

<template>
  <main>
    <header class="w-100 bg-light">
      <nav class="navbar navbar-expand-lg w-95">
        <div class="container-fluid p-0">
          <a class="navbar-brand" href="#">
            <img src="./assets/images/logo-company.jpg" alt="Logo" width="200px">
          </a>

          <div class="collapse navbar-collapse justify-content-end" id="navbarNav">
            <ul class="navbar-nav">
              <li class="nav-item me-4">
                <a class="nav-link fw-bold" aria-current="page" href="#">Lý do nên đầu tư vào Vietnam Tourist</a>
              </li>
              <li class="nav-item me-4">
                <a class="nav-link fw-bold" href="#">Về chúng tôi</a>
              </li>
              <li class="nav-item me-4">
                <a class="nav-link fw-bold" href="#">Ưu điểm khi chọn đầu tư</a>
              </li>
              <li class="nav-item me-4">
                <a class="nav-link fw-bold" href="#">Đặc quyền cao cấp dành riêng</a>
              </li>
              <li class="nav-item me-4">
                <a class="nav-link fw-bold" href="#">Mục tiêu IPO 2028</a>
              </li>
            </ul>
          </div>

          <div class="btn-container">
            <button class="page-btn">Đăng ký tư vấn</button>
          </div>

        </div>
      </nav>
    </header>

    <!-- Body part -->
    <HomeView />

    <footer style="background-color: #f7f7f7;">
      <div class="p-70" style="width: 85%; margin: auto;">
        <div class="contact_container d-flex" style="padding-bottom: 50px;">
          <div class="firm_container">

            <div class="title fw-bold fs-5">Điều khoản</div>
            <div class="firm-items_container mt-4">
              <div class="firm-item mb-2">Nội quy</div>
              <div class="firm-item">Chính sách bảo mật</div>
            </div>

          </div>

          <div class="contact_container ms-5">
            <div class="title fw-bold fs-5">Kết nối</div>

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

              <div class="contact-item company-email mb-2">
                info@vietnamtouristvn.vn
              </div>

              <div class="contact-item company-phone mb-2">
                (028) 3636 0292 - (028) 3636 0293
              </div>
            </div>

          </div>
        </div>

        <hr style="color: #c6c6c6;">

        <div class="fin_container d-flex align-items-center" style="padding-top: 50px;">
          <div class="img-wrapper" style="width: 40%;">
            <img src="./assets/images/logo-company.jpg" alt="">
          </div>

          <div class="company-information">
            <div class="company-title text-uppercase fs-3 fw-medium" style="color: #005ea0;">Công ty CP Thương mại và dịch vụ du lịch Vietnam Tourist</div>
            <div class="information_container d-flex">
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
    </footer>
  </main>
</template>

<style>
/* Adding responsive */
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
  margin: 70px 0;
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
</style>
