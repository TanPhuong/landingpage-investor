<script setup>
const data = [
  {
    title: "Lợi nhuận",
    economicDetail: "Lãi suất 1,0 - 4,0%/năm",
    invesmentDetail: "🤑 Lợi nhuận lên đến 20%/năm"
  },
  {
    title: "Tăng trưởng giá trị tài sản",
    economicDetail: "Ít có sự gia tăng",
    invesmentDetail: "😱 Tăng gấp 3-30 lần mỗi năm"
  },
  {
    title: "Mức đầu tư ban đầu",
    economicDetail: "Không yêu cầu tối thiểu",
    invesmentDetail: "💵 Chỉ từ 10 triệu đồng"
  },
  {
    title: "Rủi ro an toàn",
    economicDetail: "An toàn cao, rủi ro thấp",
    invesmentDetail: "✅ Lợi nhuận cao, mức rủi ro có quản lý"
  },
  {
    title: "Tác động cộng đồng",
    economicDetail: "Không có",
    invesmentDetail: "🏝 Phát triển ngành du lịch Việt Nam"
  },
]
</script>

<template>
  <main>
    <!-- Form register section -->
    <div id="form-register_section">
      <div class="w-95 d-flex justify-content-end" style="padding: 180px 0;">
        <div class="form-register_container" style="width: 40%;">
          <div class="p-4">
            <div class="title-section fw-semibold fs-3 mb-4">👉 Đăng ký nhận tư vấn đầu tư!</div>

            <form action="submit">
              <!-- Name input -->
              <div class="mb-3">
                <label for="nameInput" class="form-label fw-semibold">Họ và tên
                  <span class="text-danger">(*)</span></label>
                <input type="text" class="form-control input-investor" id="nameInput"
                  placeholder="Nhập Họ và tên của bạn">
              </div>

              <!-- phone and email input -->
              <div class="mb-3 row">
                <div class="col-6">
                  <label for="phoneInput" class="form-label fw-semibold">Số điện thoại
                    <span class="text-danger">(*)</span></label>
                  <input type="number" class="form-control input-investor" id="phoneInput"
                    placeholder="Nhập số điện thoại của bạn">
                </div>
                <div class="col-6">
                  <label for="emailInput" class="form-label fw-semibold">Email
                    <span class="text-danger">(*)</span></label>
                  <input type="email" class="form-control input-investor" id="emailInput"
                    placeholder="Nhập email của bạn">
                </div>
              </div>

              <!-- investment -->
              <div class="mb-3">
                <label for="investmentInput" class="form-label fw-semibold">Số tiền dự định đầu tư
                  <span class="text-danger">(*)</span></label>
                <select name="investmentInput" id="investmentInput" class="form-select form-select-sm input-investor">
                  <option selected>Chọn số tiền dự định đầu tư</option>
                </select>
              </div>

              <!-- city -->
              <div class="mb-3">
                <label for="cityInput" class="form-label fw-semibold">Tỉnh/Thành phố
                  <span class="text-danger">(*)</span></label>
                <select name="cityInput" id="cityInput" class="form-select form-select-sm input-investor">
                  <option selected class="fw-bold">Chọn Tỉnh/Thành phố</option>
                </select>
              </div>

              <div class="d-flex justify-content-center">
                <button type="submit" class="page-btn">Gửi thông tin</button>
              </div>

            </form>
          </div>
        </div>
      </div>
    </div>

    <!-- Reason section -->
    <div id="reason_section" class="w-95">
      <div class="p-70">
        <div class="title-section text-center fs-1 fw-semibold">
          Lý do nên chọn đầu tư vào Vietnam Tourist
        </div>

        <div class="reason-item_container d-flex justify-content-around text-center my-5" style="flex-wrap: wrap;">
          <div class="reason-item w-25">
            <div class="icon-container">
              <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" viewBox="0 0 20 20">
                <path fill="#f0578a"
                  d="M14 2.75a.75.75 0 0 1 .75-.75h2.5a.75.75 0 0 1 .75.75v2.5a.75.75 0 0 1-1.5 0v-.69l-4.47 4.47a.75.75 0 0 1-1.06 0L8.5 6.56l-4.22 4.22a.75.75 0 1 1-1.06-1.06l4.75-4.75a.75.75 0 0 1 1.06 0l2.47 2.47l3.94-3.94h-.69a.75.75 0 0 1-.75-.75M3.75 14a.75.75 0 0 1 .75.75v2.5a.75.75 0 0 1-1.5 0v-2.5a.75.75 0 0 1 .75-.75m4.75-2.25a.75.75 0 0 0-1.5 0v5.5a.75.75 0 0 0 1.5 0zM11.75 13a.75.75 0 0 1 .75.75v3.5a.75.75 0 0 1-1.5 0v-3.5a.75.75 0 0 1 .75-.75m4.75-3.25a.75.75 0 0 0-1.5 0v7.5a.75.75 0 0 0 1.5 0z" />
              </svg>
            </div>
            <div class="description w-75 text-wrap fs-5 mt-4" style="margin: auto;"><span class="fw-semibold">Tăng
                trưởng tài sản</span> nhanh hơn
              so với các
              phương thức khác</div>
          </div>

          <div class="reason-item w-25">
            <div class="icon-container">
              <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" viewBox="0 0 24 24">
                <path fill="#f0578a"
                  d="M20.04 8.71V4h-4.7L12 .69L8.71 4H4v4.71L.69 12L4 15.34v4.7h4.71L12 23.35l3.34-3.31h4.7v-4.7L23.35 12zM8.83 7.05c.98 0 1.77.79 1.77 1.78a1.77 1.77 0 0 1-1.77 1.77c-.99 0-1.78-.79-1.78-1.77c0-.99.79-1.78 1.78-1.78M15.22 17c-.98 0-1.77-.8-1.77-1.78a1.77 1.77 0 0 1 1.77-1.77c.98 0 1.78.79 1.78 1.77A1.78 1.78 0 0 1 15.22 17m-6.72.03L7 15.53L15.53 7l1.5 1.5z" />
              </svg>
            </div>
            <div class="description w-75 text-wrap fs-5 mt-4" style="margin: auto;">Tỷ suất lợi nhuận hấp dẫn lên đến
              <span class="fw-semibold">20%/năm</span>
            </div>
          </div>

          <div class="reason-item w-25">
            <div class="icon-container">
              <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" viewBox="0 0 16 16">
                <path fill="#f0578a"
                  d="M3.75 2a.75.75 0 0 0-.662.397l-2 3.75a.75.75 0 0 0 .071.815l4.934 6.316A3.3 3.3 0 0 1 6 12.5a2.5 2.5 0 0 1 1.451-2.27L6.598 7.5h.943A3 3 0 0 1 8.264 6H6.398l.625-2.5h1.954l.427 1.707a3 3 0 0 1 1.5-.18l-.38-1.527H11.8L13.133 6h-.397a2.99 2.99 0 0 1 .649 2.825l1.456-1.863a.75.75 0 0 0 .07-.815l-2-3.75A.75.75 0 0 0 12.25 2zm-.883 4L4.2 3.5h1.277L4.852 6zm.616 1.5h1.544l1.029 3.293zM12.5 8a2 2 0 1 1-4 0a2 2 0 0 1 4 0m1.5 4.5c0 1.245-1 2.5-3.5 2.5S7 13.75 7 12.5A1.5 1.5 0 0 1 8.5 11h4a1.5 1.5 0 0 1 1.5 1.5" />
              </svg>

            </div>
            <div class="description w-75 text-wrap fs-5 mt-4" style="margin: auto;">Tập trung kinh doanh và sự nghiệp mà
              vẫn <span class="fw-semibold">đầu tư
                hiệu quả</span></div>
          </div>

          <div class="reason-item w-25">
            <div class="icon-container">
              <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" viewBox="0 0 24 24">
                <path fill="#f0578a" d="M13.5 16a1.5 1.5 0 1 1-3 0a1.5 1.5 0 0 1 3 0" />
                <path fill="#f0578a"
                  d="m14.347.66l3.18 4.456l2.097-.715L21.538 10h.962v12h-21V10h.51v-.01l.648.006zM9.397 10h10.028l-1.037-3.033l-1.522.487zM7.839 8.417L15.55 5.79l-1.604-2.25zM5.5 12h-2v2a2 2 0 0 0 2-2m10 4a3.5 3.5 0 1 0-7 0a3.5 3.5 0 0 0 7 0m5 4v-2a2 2 0 0 0-2 2zm-2-8a2 2 0 0 0 2 2v-2zm-15 8h2a2 2 0 0 0-2-2z" />
              </svg>
            </div>
            <div class="description w-75 text-wrap fs-5 mt-4" style="margin: auto;">Tham gia với mức đầu tư thấp <span
                class="fw-semibold">chỉ từ
                10.000.000đ</span></div>
          </div>
        </div>
      </div>
    </div>

    <!-- Consultant section -->
    <div id="consultant_section">
      <div class="consultant_container w-95 p-70 d-flex justify-content-around align-items-center">
        <div class="img-section w-25">
          <img src="../assets/images/Model 2.png" alt="" class="block w-100">
        </div>

        <div class="detail-section" style="width: 40%;">
          <div class="intro-container">
            <div class="title-section fw-semibold fs-4" style="color: #f05083;">Kênh Đầu tư Vietnam Tourist</div>
            <div class="emphasize-text fw-bold fs-1 page-text-gradient">Cơ hội siêu hấp dẫn cho Nhà đầu tư</div>
          </div>

          <div class="description-text fw-semibold mt-2" style="text-align: justify;">Kênh đầu tư Vietnam Tourist là quỹ
            đầu tư được
            thành lập bởi Công ty Cổ phần
            Thương mại và Dịch vụ Vietnam Tourist được thành lập năm 2017,
            là một trong những doanh nghiệp lữ hành hàng đầu tại Việt Nam với mạng lưới chi nhánh trên toàn quốc, chuyên
            tổ chức tour trong nước, quốc tế</div>

          <div class="btn-container my-4">
            <button type="button" class="page-btn">Đăng ký tư vấn</button>
            <button type="button" class="ceo-mail--btn fw-semibold">Thư ngỏ từ CEO</button>
          </div>
        </div>
      </div>
    </div>

    <!-- Benefit section -->
    <div id="benefit_section">
      <div class="w-95 p-70">
        <div class="title-section text-center fs-1 fw-semibold mb-5">Ưu điểm khi đầu tư Vietnam Tourist</div>

        <!-- Adjust the color -->
        <div class="table-container w-100">
          <table class="table " style="margin: auto; width: 70%;">
            <thead>
              <tr>
                <th scope="col"></th>
                <th scope="col" class="py-4">Gửi tiết kiệm thông thường</th>
                <th scope="col" class="py-4 ps-4 page-gradient-pink text-white fs-5 text-wrap"
                  style="border-radius: 25px 25px 0 0;">Đầu tư vào quỹ Vietnam Tourist</th>
              </tr>
            </thead>

            <tbody>
              <tr v-for="(item, index) in data" :key="index">
                <th scope="row" class="py-4 ps-4">{{ item.title }}</th>
                <td class="py-4">{{ item.economicDetail }}</td>
                <td class="investment-item py-4 ps-4 page-gradient-pink text-white">{{ item.invesmentDetail }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- Privilege section -->
    <div id="privilege_section" class="page-gradient-blue">
      <div class="w-95 p-70">
        <div class="title-section text-white fs-1 fw-semibold text-center">Đặc quyền dành riêng cho cổ đông</div>

        <div class="privilege-item_container row text-center text-white my-5">
          <div class="privilege-item col">
            <div class="icon-wrapper">
              <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" viewBox="0 0 24 24">
                <path fill="#f0578a"
                  d="M5 16L3 5l5.5 5L12 4l3.5 6L21 5l-2 11zm14 3c0 .6-.4 1-1 1H6c-.6 0-1-.4-1-1v-1h14z" />
              </svg>
            </div>
            <div class="desc-wrapper">
              <div class="title-privilege fw-bold fs-5 mt-4">Chính sách đặc biệt khi mua Tour</div>
              <div class="desc-privilege w-75 fs-5 mt-2" style="margin: auto;">Cổ đông trở thành khách VIP, nhận ngay ưu
                đãi đặc biệt trên mọi chuyến đi.</div>
            </div>
          </div>

          <div class="privilege-item col">
            <div class="icon-wrapper">
              <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" viewBox="0 0 14 14">
                <path fill="#f0578a" fill-rule="evenodd"
                  d="M2 0a.5.5 0 0 0-.453.288l-1.5 3.209a.5.5 0 0 0-.045.253H0v.945c0 .524.226 1.026.63 1.396c.402.37.949.578 1.519.578h.3a2.25 2.25 0 0 0 1.52-.578q.247-.227.4-.508c.127-.17.333-.17.452-.014q.155.29.407.522c.403.37.95.578 1.52.578h.537a2.25 2.25 0 0 0 1.52-.578q.235-.217.386-.484c.131-.205.36-.2.48-.01q.153.273.392.494c.403.37.95.578 1.52.578h.268a2.25 2.25 0 0 0 1.52-.578c.403-.37.629-.872.629-1.396V3.75h-.002a.5.5 0 0 0-.045-.253l-1.5-3.209A.5.5 0 0 0 12 0zM1 13V7.729c1.188.392 2.605.217 3.578-.536c1.298 1.004 3.549 1.004 4.846 0c.978.756 2.392.928 3.576.526V13a1 1 0 0 1-1 1h-1.255v-3.79a.2.2 0 0 0-.07-.155a.25.25 0 0 0-.17-.064H8.513a.25.25 0 0 0-.17.064a.2.2 0 0 0-.07.155V14H2a1 1 0 0 1-1-1m1.502-2.24V9.5a.5.5 0 0 1 .5-.5h3.014a.5.5 0 0 1 .5.5v1.26a.5.5 0 0 1-.5.5H3.002a.5.5 0 0 1-.5-.5"
                  clip-rule="evenodd" />
              </svg>
            </div>
            <div class="desc-wrapper">
              <div class="title-privilege fw-bold fs-5 mt-4">Cơ hội trở thành Đại lý bán hàng</div>
              <div class="desc-privilege w-75 fs-5 mt-2" style="margin: auto;">Mức hoa hồng hấp dẫn, được đào tạo kỹ
                năng
                chuyên nghiệp - bài bản.
              </div>
            </div>
          </div>

          <div class="privilege-item col">
            <div class="icon-wrapper">
              <svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" viewBox="0 0 1024 1024">
                <path fill="#f0578a"
                  d="M640 832H64V640a128 128 0 1 0 0-256V192h576v160h64V192h256v192a128 128 0 1 0 0 256v192H704V672h-64zm0-416v192h64V416z" />
              </svg>
            </div>
            <div class="desc-wrapper">
              <div class="title-privilege fw-bold fs-5 mt-4">Tặng vé du lịch miễn phí 100%</div>
              <div class="desc-privilege w-75 fs-5 mt-2" style="margin: auto;">Trải nghiệm những chuyến du lịch miễn phí
                hoàn toàn từ Vietnam
                Tourist.</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Growth section -->
    <div id="growth_section">
      <div class="growth_container w-95 d-flex justify-content-center align-items-center" style="padding-top: 100px;">
        <div class="img-section w-25">
          <img src="../assets/images/Model 3 copy.png" alt="" class="w-100 block">
        </div>

        <div class="detail-section" style="margin-left: 150px; width: 40%;">
          <div class="emphasize-text fw-bold fs-1 page-text-gradient">Giá trị đầu tư tăng gấp 3-30 lần/năm</div>

          <div class="description-text mt-3 fw-semibold" style="text-align: justify;">Vietnam Tourist cam kết minh bạch
            tài chính với báo
            cáo chi tiết hàng quý và từng năm, đảm bảo mục tiêu phát triển rõ ràng.
            Đồng hành cùng chúng tôi để gia tăng tài sản bền vừng!
          </div>

          <div class="btn-container my-4">
            <button type="button" class="page-btn">Đăng ký tư vấn</button>
          </div>
        </div>

      </div>
    </div>

    <!-- Representative section -->
    <div id="representative_section">
      <div class="representative_container w-95 p-70 d-flex align-items-center justify-content-center">
        <div class="commit_container" style="width: 30%;">
          <div class="title-section fw-semibold fs-4" style="color: #f05083;">Với niềm đam mê khát khao phát triển trong
            ngành du lịch</div>

          <div class="commit-text fw-semibold fs-1">Vietnam Tourist cam kết luôn đồng hành và tạo nên giá trị cùng quý
            cổ đông</div>
          <hr>

          <div class="ceo_container d-flex align-items-center">
            <div class="ceo-name">
              <p class="fw-bold fs-5 m-0" style="color: #005ea0;">Phạm Anh Nhân</p>
              <p class="m-0">CEO of Vietnam Tourist</p>
            </div>

            <div class="btn-container ms-5">
              <button type="button" class="page-btn">Đăng ký tư vấn</button>
            </div>
          </div>
        </div>

        <div class="ceo-portrait text-center position-relative" style="width: 40%;">
          <img src="../assets/images/ceo.jpg" alt="" class="w-75 block" style="border-radius: 15%;">

          <div class="weird-div fs-1 position-absolute rounded-circle page-gradient-blue">
            <svg xmlns="http://www.w3.org/2000/svg" width="75%" height="75%" viewBox="0 0 20 20">
              <path fill="#fff"
                d="m7 6l1-2H6C3.79 4 2 6.79 2 9v7h7V9H5c0-3 2-3 2-3m7 3c0-3 2-3 2-3l1-2h-2c-2.21 0-4 2.79-4 5v7h7V9z" />
            </svg>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
/* Form register section */
#form-register_section {
  /* background-color: #005ea0; */
  background-image: url(../assets/images/Banner.png);
  background-size: cover;
  background-repeat: no-repeat;


  & .form-register_container {
    background-color: #fff;
    border-radius: 10px;
  }
}

.title-section {
  color: #005ea0;
}

.input-investor {
  border: 2px solid #d9d9d9;
  border-radius: 10px;
}

select.input-investor {
  padding: 6px 12px;
  font-weight: 500;
}

Ư .input-investor::placeholder {
  padding: 4px;
  font-size: 14px;
  color: #d9d9d9;
  font-weight: 400;
}

/* Reason section */
#reason_section {

  & .icon-container {
    width: 80px;
    height: 80px;
    padding: 15px;
    margin: auto;
    background-color: #feeff4;
    border: 2px solid #005ea0;
    border-radius: 20px;
  }
}

/* consultant_section */
#consultant_section {
  background-color: #f1f9ff;
}

.ceo-mail--btn {
  padding: 12px 25px;
  margin-left: 20px;
  border: 2px solid #005ea0;
  border-radius: 15px;
  color: #005ea0;
  background-color: transparent;
}

.ceo-mail--btn:hover {
  color: #f05083;
}

/* Benefit section */
tbody tr:last-child {
  border: none;

  & th {
    border: none;
  }

  & td {
    border: none;
  }

  & .investment-item {
    border-radius: 0 0 25px 25px;
  }
}

#privilege_section {

  & .icon-wrapper {
    width: 90px;
    height: 90px;
    padding: 20px;
    margin: auto;
    background-color: #fff;
    border-radius: 25px;
  }
}

#growth_section {
  background-image: url(../assets/images/growth-background.avif);
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}

/* Representation section */
.weird-div {
  width: 100px;
  height: 100px;
  padding: 15px;
  bottom: 40%;
  left: 5%;
}

@media (max-width: 1024px) {

  #form-register_section {
    
  }


  #reason_section {

    & .reason-item_container .reason-item {
      width: 50% !important;
      margin-top: 10px;
    }
  }

  .consultant_container {
    display: block !important;

    & .detail-section {
      width: 100% !important;
      position: relative;
    }

    & .img-section {
      width: 100% !important;
      text-align: center;
      margin-top: 70px;
      padding: 50px;

      & img {
        width: 80% !important;
      }
    }

    & .intro-container {
      text-align: center;
      position: absolute;
      top: -200%;
    }

    & .btn-container {
      display: flex;
      justify-content: center;
    }
  }

  #benefit_section {

    & .table-container table {
      width: 100% !important;
      font-size: 14px !important;

      & .investment-item {
        padding: 24px 10px !important;
      }
    }
  }

  #privilege_section {

    & .privilege-item_container {
      display: flex !important;
      flex-direction: column !important;
      margin-top: 30px !important;

      & .privilege-item {
        display: flex !important;
        margin-top: 20px;

        & .icon-wrapper {
          width: 80px;
          height: 60px;
          padding: 5px 10px;
          border-radius: 15px;
        }

        & .desc-wrapper {
          text-align: left;
          margin-left: 20px;
        }

        & .title-privilege {
          font-size: 18px !important;
        }

        & .desc-privilege {
          font-size: 16px !important;
          width: 100% !important;
          margin: 0 !important;
          padding-top: 8px;
        }
      }
    }
  }

  #growth_section .growth_container {
    display: block !important;

    & .img-section {
      width: 100% !important;
      text-align: center;

      & img {
        width: 80% !important;
        padding: 25px
      }
    }

    & .detail-section {
      width: 100% !important;
      margin-left: 0 !important;
      position: relative;

      & .emphasize-text {
        position: absolute;
        top: -300%;
        text-align: center;
      }

      & .btn-container {
        display: flex;
        justify-content: center;
      }
    }
  }

  #representative_section .representative_container {
    flex-direction: row-reverse;
    align-items: start !important;

    & .commit_container {
      width: 60% !important;
      margin-left: 10px;

      & .title-section {
        font-size: 16px !important;
      }

      & .commit-text {
        font-size: 24px !important;
      }

      & .btn-container {
        display: none !important;
      }
    }

    & .ceo-portrait {

      & img {
        width: 90% !important;
      }

      & .weird-div {
        display: none !important;
      }
    }
  }
}
</style>
