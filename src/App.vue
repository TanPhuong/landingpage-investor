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

    <footer>

    </footer>
  </main>
</template>

<style>
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

.p-section {
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

.nav-item:hover a{
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
