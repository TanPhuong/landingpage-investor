<template>
    <nav class="navbar w-95">
        <div class="container-fluid p-0">
            <!-- Logo -->
            <a class="navbar-brand w-25" href="#">
                <img src="../assets/images/logo-transparent-2.png" alt="Logo" class="w-100">
            </a>

            <div class="d-flex align-items-center" style="width: auto;">
                <div class="btn-container me-3">
                    <button class="page-btn" style="font-size: 14px;">Đăng ký tư vấn</button>
                </div>
    
                <button class="navbar-toggler" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasNavbar"
                    aria-controls="offcanvasNavbar" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
    
                <div class="offcanvas offcanvas-top" tabindex="-1" id="offcanvasNavbar"
                    aria-labelledby="offcanvasNavbarLabel">
                    <div class="offcanvas-header">
                        
                        <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
                    </div>
                    <div class="offcanvas-body">
                        <ul class="navbar-nav justify-content-end flex-grow-1 pe-3">
                            <li class="nav-item">
                                <a class="nav-link fw-bold" aria-current="page" href="#">Lý do nên đầu tư vào Vietnam
                                    Tourist</a>
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
                        </ul>
                    </div>
                </div>
            </div>

        </div>
    </nav>

</template>