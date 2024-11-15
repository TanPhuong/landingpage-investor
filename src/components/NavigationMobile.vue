<template>
    <nav class="navbar p-0">
        <div class="container-fluid p-0">
            <!-- Logo -->
            <a class="navbar-brand w-25 p-0 m-0" href="#">
                <img src="../assets/images/logo-transparent-2.png" alt="Logo" class="w-100 block">
            </a>

            <div class="d-flex align-items-center" style="width: auto;">
                <div class="btn-container me-3">
                    <button class="page-btn" style="font-size: 14px;">Đăng ký tư vấn</button>
                </div>

                <button class="navbar-toggler p-0" type="button" data-bs-toggle="offcanvas"
                    data-bs-target="#offcanvasNavbar" aria-controls="offcanvasNavbar" aria-label="Toggle navigation"
                    style="border: none;">
                    <span class="navbar-toggler-icon"></span>
                </button>

                <div class="offcanvas offcanvas-top" tabindex="-1" id="offcanvasNavbar"
                    aria-labelledby="offcanvasNavbarLabel" style="height: 100vh;">
                    <div class="offcanvas-header justify-content-between">

                        <!-- Logo -->
                        <a class="navbar-brand w-25 p-0 m-0" href="#">
                            <img src="../assets/images/logo-transparent-2.png" alt="Logo" class="w-100 block">
                        </a>

                        <div class="btn-container">
                            <button class="page-btn" style="font-size: 14px;">Đăng ký tư vấn</button>
                            <button type="button" class="btn btn-close" data-bs-dismiss="offcanvas"
                                aria-label="Close"></button>
                        </div>

                    </div>
                    <div class="offcanvas-body">
                        <ul class="navbar-nav justify-content-end flex-grow-1 pe-3">
                            <li class="nav-item">
                                <a class="nav-link aver-semi-bold" aria-current="page" href="#reason_section">Lý do nên
                                    đầu tư vào Vietnam Tourist</a>
                            </li>
                            <li class="nav-item">
                                <a class="nav-link aver-semi-bold" href="#consultant_section">Về chúng tôi</a>
                            </li>
                            <li class="nav-item">
                                <a class="nav-link aver-semi-bold" href="#benefit_section">Ưu điểm khi chọn đầu tư</a>
                            </li>
                            <li class="nav-item">
                                <a class="nav-link aver-semi-bold" href="#privilege_section">Đặc quyền cao cấp dành
                                    riêng</a>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>

        </div>
    </nav>
</template>

<style scoped>
@media (max-width: 1024px) {
    nav {

        & .navbar-brand {
            min-width: 100px;
            max-height: 40px;
        }
    }

    .offcanvas-header {
        box-shadow: 0 0 6px #cccbcb;

        & .btn-close {
            width: 24px;
            height: 24px;
            padding: 0;
        }

        & .page-btn {
            margin-right: 16px;
        }
    }

    .offcanvas-body {

        & .nav-item {
            margin-bottom: 32px;

            & a {
                padding: 0;

                font-size: 14px;
                color: #000;
            }
        }

        & .nav-item:hover a {
            color: #005ea0;
        }
    }



}
</style>