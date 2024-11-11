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
      <div class="w-95 d-flex justify-content-between" style="padding: 30px 0;">
        <div class="introduction-text text-white w-50">

          <div class="container">
            <div class="company-name text-uppercase fw-semibold fs-1" style="letter-spacing: 1px;">Vietnam Tourist</div>
            <div class="company-slogan text-capitalize fst-italic fw-medium fs-5">"An tâm đầu tư - Tài sản vững bền"
            </div>
          </div>
        </div>

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
      <div class="py-5">
        <div class="title-section text-center fs-1 fw-semibold">
          Lý do nên chọn đầu tư vào Vietnam Tourist
        </div>

        <div class="reason-item_container d-flex justify-content-around text-center my-5">
          <div class="reason-item">
            <div class="icon"></div>
            <div class="description text-wrap"><span class="fw-semibold">Tăng trưởng tài sản</span> nhanh hơn so với các
              phương thức khác</div>
          </div>

          <div class="reason-item">
            <div class="icon"></div>
            <div class="description text-wrap">Tỷ suất lợi nhuận hấp dẫn lên đến <span
                class="fw-semibold">20%/năm</span></div>
          </div>

          <div class="reason-item">
            <div class="icon"></div>
            <div class="description text-wrap">Tập trung kinh doanh và sự nghiệp mà vẫn <span class="fw-semibold">đầu tư
                hiệu quả</span></div>
          </div>

          <div class="reason-item">
            <div class="icon"></div>
            <div class="description text-wrap">Tham gia với mức đầu tư thấp <span class="fw-semibold"> chỉ từ
                10.000.000đ</span></div>
          </div>
        </div>
      </div>
    </div>

    <!-- Consultant section -->
    <div id="consultant_section">
      <div class="w-95 py-5 d-flex justify-content-around">
        <div class="img-section w-25 rounded-circle page-gradient-blue">
          <!-- <img src="" alt=""> -->

        </div>

        <div class="detail-section" style="width: 40%;">
          <div class="title-section fw-semibold fs-4" style="color: #f05083;">Kênh Đầu tư Vietnam Tourist</div>
          <div class="emphasize-text fw-bold fs-1 page-text-gradient">Cơ hội siêu hấp dẫn cho Nhà đầu tư</div>

          <div class="description-text" style="text-align: justify;">Kênh đầu tư Vietnam Tourist là quỹ đầu tư được
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
      <div class="w-95 py-5">
        <div class="title-section text-center fs-1 fw-semibold mb-5">Ưu điểm khi đầu tư Vietnam Tourist</div>

        <!-- Adjust the color -->
        <div class="table-container w-100">
          <table class="table " style="margin: auto; width: 70%;">
            <thead>
              <tr>
                <th scope="col"></th>
                <th scope="col" class="py-4">Gửi tiết kiệm thông thường</th>
                <th scope="col" class="py-4 ps-4 page-gradient-pink text-white fs-5 text-wrap" style="border-radius: 25px 25px 0 0;">Đầu tư vào quỹ Vietnam Tourist</th>
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
      <div class="w-95 py-5">
        <div class="title-section text-white fs-1 fw-semibold text-center">Đặc quyền dành riêng cho cổ đông</div>

        <div class="privilege-item_container row text-center text-white my-5">
          <div class="privilege-item col">
            <div class="icon">

            </div>

            <div class="title-privilege fw-bold">Chính sách đặc biệt khi mua Tour</div>
            <div class="desc-privilege">Cổ đông trở thành khách VIP, nhận ngay ưu đãi đặc biệt trên mọi chuyến đi.</div>
          </div>

          <div class="privilege-item col">
            <div class="icon">

            </div>

            <div class="title-privilege fw-bold">Cơ hội trở thành Đại lý bán hàng</div>
            <div class="desc-privilege">Mức hoa hồng hấp dẫn, được đào tạo kỹ năng chuyên nghiệp - bài bản.</div>
          </div>

          <div class="privilege-item col">
            <div class="icon">

            </div>

            <div class="title-privilege fw-bold">Tặng vé du lịch miễn phí 100%</div>
            <div class="desc-privilege">Trải nghiệm những chuyến du lịch miễn phí hoàn toàn từ Vietnam Tourist.</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Growth section -->
    <div id="growth_section">
      <div class="w-95 py-5 d-flex justify-content-around">
        <div class="img-section w-25 ">
          <!-- <img src="" alt=""> -->

        </div>

        <div class="detail-section" style="width: 40%;">
          <div class="emphasize-text fw-bold fs-1 page-text-gradient">Giá trị đầu tư tăng gấp 3-30 lần/năm</div>

          <div class="description-text" style="text-align: justify;">Vietnam Tourist cam kết minh bạch tài chính với báo cáo chi tiết hàng quý và từng năm, đảm bảo mục tiêu phát triển rõ ràng. 
            Đồng hành cùng chúng tôi để gia tăng tài sản bền vừng!
          </div>

          <div class="btn-container my-4">
            <button type="button" class="page-btn">Đăng ký tư vấn</button>
          </div>
        </div>

      </div>
    </div>
    <!-- Representative section -->
  </main>
</template>

<style scoped>
/* Form register section */
#form-register_section {
  background-color: #005ea0;

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

.input-investor::placeholder {
  padding: 4px;
  font-size: 14px;
  color: #d9d9d9;
  font-weight: 400;
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

#growth_section {
  background-image: url(../assets/images/growth-background.avif);
  background-repeat: no-repeat;
  background-position: center;
  background-attachment: fixed;
  background-size: cover;
}
</style>
