<script setup>
import ModalForm from '@/components/ModalForm.vue';
import LetterForm from '@/components/LetterForm.vue';
import axios from 'axios';
import { onMounted, reactive, ref, toRaw } from 'vue';

const props = defineProps({
  mobileView: {
    type: Boolean,
    required: true
  }
})

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
    invesmentDetail: "💵 Chỉ từ 10 đồng"
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

const moneyList = [10000000, 20000000, 30000000, 50000000, 100000000, 200000000, 500000000, 1000000000]

// API to get VN provinces
const vnProvincesAPI = "https://provinces.open-api.vn/api/p/"; 

let provincesData = ref([]);
let cleanedProvincesData = ref([])
let isLoading = ref(false)

onMounted(async () => {
  await fetch(vnProvincesAPI)
    .then(res => res.json())
    .then(data => {
      provincesData.value = data.map(p => p.name)

      cleanedProvincesData.value = provincesData.value.map((province) =>
        province.replace("Tỉnh ", "")
      );

      console.log(cleanedProvincesData);
    })
    .catch(error => console.log('ERROR' + error))
})

let formData = reactive({
  name: "",
  phone: "",
  email: "",
  investment: "Chọn số tiền dự định đầu tư",
  provinces: "Chọn Tỉnh/Thành phố"
})

const submitFormAPI = "http://localhost:3000/api/email/sendEmail";

const handleSubmit = async (e) => {
  e.preventDefault() 
  isLoading.value = true
  const res = await axios.post(submitFormAPI, toRaw(formData));
  
  console.log(toRaw(formData));
  console.log(res)

  isLoading = false;
  location.reload();
}

</script>

<template>
  <main>

    <ModalForm 
      :mobile-view="mobileView" 
      :cleaned-provinces-data="cleanedProvincesData"
      />

    <LetterForm :mobile-view="mobileView" />

    <div class="img-section w-100" v-if="props.mobileView">
      <img src="../assets/images/Pop-up.png" alt="" class="block w-100">
    </div>

    <!-- Form register section -->
    <div id="form-register_section" class="d-flex">
      <div class="form-register_wrapper w-95 d-flex justify-content-end">
        <div class="form-register_container">
          <div class="container">
            <div class="aver-semi-bold fs-3 mb-3">👉 <span class="page-text-gradient">Đăng ký nhận tư vấn đầu tư!</span>
            </div>

            <form method="post" @submit="handleSubmit">
              <!-- Name input -->
              <div class="register-item mb-3">
                <label for="nameInput" class="form-label aver-semi-bold">Họ và tên
                  <span class="page-text-gradient-pink">(*)</span></label>
                <input required type="text" class="form-control input-investor" id="nameInput" v-model="formData.name" 
                  placeholder="Nhập Họ và tên của bạn">
              </div>

              <!-- phone and email input -->
              <div class="register-item_wrapper mb-3 row">
                <div class="register-item col-6">
                  <label for="phoneInput" class="form-label aver-semi-bold">Số điện thoại
                    <span class="page-text-gradient-pink">(*)</span></label>
                  <input required type="number" pattern="[0-9]" class="form-control input-investor" id="phoneInput" v-model.number="formData.phone"
                    placeholder="Nhập số điện thoại của bạn">
                </div>

                <div class="register-item col-6">
                  <label for="emailInput" class="form-label aver-semi-bold">Email
                    <span class="page-text-gradient-pink">(*)</span></label>
                  <input required type="email" class="form-control input-investor" id="emailInput" v-model="formData.email"
                    placeholder="Nhập email của bạn">
                </div>
              </div>

              <!-- investment -->
              <div class="register-item mb-3">
                <label for="investmentInput" class="form-label aver-semi-bold">Số tiền dự định đầu tư
                  <span class="page-text-gradient-pink">(*)</span></label>
                <select name="investmentInput" id="investmentInput"
                  class="form-select form-select-sm input-investor aver-semi-bold" v-model="formData.investment">
                  <option disabled>Chọn số tiền dự định đầu tư</option>
                  <option v-for="(money, index) in moneyList" :key="index">{{ money.toLocaleString() }} đ</option>
                </select>
              </div>

              <!-- provinces -->
              <div class="register-item mb-4">
                <label for="cityInput" class="form-label aver-semi-bold">Tỉnh/Thành phố</label>
                <select name="cityInput" id="cityInput"  
                  class="form-select form-select-sm input-investor aver-semi-bold" v-model="formData.provinces">
                  <option disabled>Chọn Tỉnh/Thành phố</option>
                  <option v-for="(item, index) in cleanedProvincesData" :key="index">{{ item }}</option>
                </select>
              </div>

              <div class="d-flex justify-content-center">
                <button type="submit" class="page-btn" v-if="!isLoading">Gửi thông tin</button>
                <button type="submit" class="page-btn" v-else>Đang gửi...</button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>

    <!-- Reason section -->
    <div id="reason_section" class="section-scroll-margin m-side-100">
      <div class="reason_container p-120">
        <div class="title-section text-center aver-bold page-text-gradient">
          Lý do nên chọn đầu tư vào Vietnam Tourist
        </div>

        <div class="reason-item_container d-flex justify-content-between text-center">

          <div class="reason-item">
            <div class="icon-container">
              <svg width="45%" height="45%" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                <g clip-path="url(#clip0_187_11263)">
                  <path fill="#f0578a"
                    d="M35.2499 16.9692C28.271 16.9692 22.5938 22.6464 22.5938 29.6253C22.5938 36.6042 28.2709 42.2814 35.2498 42.2814C42.2288 42.2814 47.9996 36.6042 47.9996 29.6253C47.9996 22.6464 42.2288 16.9692 35.2499 16.9692ZM36.6931 36.4024C36.6809 36.4069 36.6682 36.4048 36.656 36.4091V38.0627C36.656 38.84 36.027 39.469 35.2497 39.469C34.4724 39.469 33.8435 38.84 33.8435 38.0627V36.3995C32.9173 36.0866 32.0299 35.4927 31.2713 34.5883C30.7714 33.9937 30.8483 33.1065 31.4443 32.6081C32.039 32.1082 32.9288 32.1851 33.4246 32.7811C34.1689 33.6669 35.0108 34.0184 35.7304 33.7602C36.2838 33.5584 36.656 33.0269 36.656 32.4378C36.656 31.6619 36.0256 31.0316 35.2497 31.0316C32.9234 31.0316 31.0311 29.1391 31.0311 26.8129C31.03 25.9836 31.2738 25.1724 31.7319 24.481C32.1899 23.7897 32.8419 23.2489 33.606 22.9266C33.6834 22.8938 33.7655 22.8956 33.8436 22.8677V21.188C33.8436 20.4107 34.4725 19.7817 35.2498 19.7817C36.0271 19.7817 36.6561 20.4107 36.6561 21.188V22.8702C37.3842 23.1162 38.0943 23.5073 38.7283 24.1213C39.2858 24.6611 39.2996 25.5509 38.7585 26.1099C38.2188 26.6674 37.3275 26.6798 36.77 26.1401C36.0861 25.4768 35.3294 25.2488 34.7032 25.5166C34.4482 25.6241 34.2306 25.8044 34.0776 26.035C33.9247 26.2656 33.8432 26.5363 33.8435 26.813C33.8435 27.5889 34.4739 28.2192 35.2497 28.2192C37.576 28.2192 39.4684 30.1117 39.4684 32.4379C39.4686 34.2052 38.3534 35.7982 36.6931 36.4024ZM1.40663 31.0316C0.629346 31.0316 0.000377655 31.6605 0.000377655 32.4378V46.5939C0.000377655 47.3711 0.629346 48.0001 1.40663 48.0001H5.62528V31.0316H1.40663Z" />
                  <path fill="#f0578a"
                    d="M33.352 8.7773L23.5084 0.339891C22.9838 -0.113297 22.2038 -0.113297 21.6791 0.339891L11.8356 8.7773C11.6171 8.96384 11.4612 9.21299 11.389 9.49103C11.3168 9.76907 11.3317 10.0626 11.4318 10.3319C11.5311 10.6015 11.7108 10.8342 11.9466 10.9985C12.1823 11.1628 12.4628 11.2508 12.7502 11.2506H16.9688V48.0001H26.8125C27.5898 48.0001 28.2188 47.3712 28.2188 46.5939V43.3863C23.2179 40.8205 19.7813 35.622 19.7813 29.6254C19.7813 23.6289 23.218 18.4304 28.2188 15.8645V11.2507H32.4374C32.7248 11.2509 33.0053 11.1629 33.241 10.9986C33.4768 10.8343 33.6565 10.6016 33.7558 10.332C33.8559 10.0627 33.8709 9.76913 33.7987 9.49106C33.7264 9.21299 33.5705 8.96383 33.352 8.7773Z" />
                  <path fill="#f0578a"
                    d="M9.93769 19.7817C9.16041 19.7817 8.53144 20.4107 8.53144 21.188V48H14.1563V19.7817H9.93769Z" />
                </g>
                <defs>
                  <clipPath id="clip0_187_11263">
                    <rect width="100%" height="100%" fill="white" />
                  </clipPath>
                </defs>
              </svg>
            </div>
            <div class="description mt-4"><span class="aver-semi-bold">Tăng trưởng tài sản</span>
              nhanh hơn so với các phương thức khác</div>
          </div>

          <div class="reason-item">
            <div class="icon-container">
              <svg width="45%" height="45%" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path fill="#f0578a"
                  d="M24.6968 1.1416C24.5063 1.14585 24.3197 1.19579 24.1525 1.28723C21.527 2.72333 19.9201 5.02399 18.0432 6.41261C15.7089 6.38143 13.0602 5.45238 10.0903 5.81982C9.87748 5.84612 9.67578 5.92946 9.5065 6.06101C9.33721 6.19255 9.20664 6.36742 9.1286 6.5671C8.04081 9.35497 8.28707 12.1503 7.74175 14.4205C5.93361 15.8966 3.30909 16.888 1.26992 19.0781C1.12381 19.235 1.02283 19.4285 0.977669 19.6381C0.932509 19.8477 0.944849 20.0655 1.01338 20.2687C1.97185 23.104 3.95857 25.0869 4.99959 27.176C4.56377 29.4696 3.18897 31.9162 3.03554 34.905C3.02445 35.1192 3.07148 35.3323 3.17165 35.522C3.27183 35.7116 3.42143 35.8706 3.6046 35.9821C6.16144 37.5384 8.95746 37.78 11.0987 38.7112C12.2382 40.7482 12.7576 43.506 14.5605 45.8942C14.6897 46.0653 14.8629 46.1983 15.0615 46.2791C15.2602 46.3599 15.477 46.3854 15.689 46.353C18.6477 45.9016 20.9448 44.2898 23.1831 43.6268C25.3658 44.4545 27.5371 46.2336 30.4536 46.9044C30.6626 46.9523 30.8806 46.9428 31.0846 46.8769C31.2887 46.8111 31.4711 46.6913 31.6126 46.5302C33.5887 44.283 34.3126 41.5713 35.6016 39.6247C37.7974 38.8582 40.6197 38.8221 43.2782 37.4615C43.4689 37.3638 43.6297 37.2165 43.7435 37.035C43.8573 36.8535 43.92 36.6446 43.9249 36.4304C43.994 33.4391 42.8052 30.8968 42.5412 28.5774C43.7353 26.5715 45.8637 24.7417 47.0306 21.9858C47.2006 21.5836 47.1369 21.1205 46.864 20.7796C44.9942 18.4432 42.4498 17.2594 40.7564 15.6525C40.3819 13.3483 40.8369 10.5785 39.9592 7.71726C39.8963 7.51229 39.7791 7.32814 39.6202 7.1843C39.4612 7.04047 39.2662 6.94229 39.056 6.90017C36.1222 6.31234 33.4115 7.04119 31.0818 6.89875C29.3137 5.37443 27.8815 2.96109 25.37 1.33365C25.1699 1.20378 24.9353 1.13711 24.6968 1.14231V1.1416ZM19.3549 14.3886C21.6134 14.3886 23.4701 16.2449 23.4701 18.5038C23.4701 20.7623 21.6134 22.6186 19.3549 22.6186C17.0961 22.6186 15.239 20.7623 15.239 18.5038C15.239 16.2449 17.0957 14.3886 19.3549 14.3886ZM31.8132 15.1274C32.1266 15.1295 32.4265 15.2553 32.6476 15.4774C32.7578 15.5881 32.8452 15.7193 32.9047 15.8637C32.9641 16.0081 32.9946 16.1628 32.9942 16.319C32.9939 16.4752 32.9628 16.6297 32.9027 16.7739C32.8426 16.918 32.7547 17.0489 32.6441 17.1591L17.0992 32.6362C16.8758 32.8585 16.5731 32.9829 16.2579 32.9822C15.9427 32.9814 15.6407 32.8554 15.4183 32.632C15.1959 32.4086 15.0714 32.106 15.072 31.7908C15.0727 31.4755 15.1985 31.1735 15.4219 30.951L30.9663 15.4739C31.0776 15.3631 31.2097 15.2754 31.3551 15.2159C31.5004 15.1564 31.6561 15.1263 31.8132 15.1274ZM19.3549 16.7661C18.3809 16.7661 17.6173 17.5297 17.6173 18.5038C17.6173 19.4775 18.3809 20.2414 19.3549 20.2414C20.3286 20.2414 21.0925 19.4775 21.0925 18.5038C21.0925 17.5297 20.3286 16.7661 19.3549 16.7661ZM29.4317 25.1113C31.6906 25.1113 33.5469 26.968 33.5469 29.2265C33.5469 31.4853 31.6902 33.3424 29.4317 33.3424C27.1728 33.3424 25.3158 31.4857 25.3158 29.2265C25.3158 26.968 27.1728 25.1113 29.4317 25.1113ZM29.4317 27.4896C28.458 27.4896 27.6937 28.2528 27.6937 29.2265C27.6937 30.2002 28.458 30.9641 29.4317 30.9641C30.4054 30.9641 31.1693 30.2005 31.1693 29.2265C31.1693 28.2524 30.4054 27.4896 29.4317 27.4896Z" />
              </svg>
            </div>
            <div class="description mt-4">Tỷ suất lợi nhuận hấp dẫn lên đến
              <span class="aver-semi-bold">20%/năm</span>
            </div>
          </div>

          <div class="reason-item ">
            <div class="icon-container">

              <svg width="45%" height="45%" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path fill="#f0578a"
                  d="M17.25 6.75C17.25 7.74456 16.8549 8.69839 16.1517 9.40165C15.4484 10.1049 14.4946 10.5 13.5 10.5C12.5054 10.5 11.5516 10.1049 10.8483 9.40165C10.1451 8.69839 9.75 7.74456 9.75 6.75C9.75 5.75544 10.1451 4.80161 10.8483 4.09835C11.5516 3.39509 12.5054 3 13.5 3C14.4946 3 15.4484 3.39509 16.1517 4.09835C16.8549 4.80161 17.25 5.75544 17.25 6.75ZM39 27.75V45H3V41.25C3 41.0511 3.07902 40.8603 3.21967 40.7197C3.36032 40.579 3.55109 40.5 3.75 40.5H12V36.75C12 36.5511 12.079 36.3603 12.2197 36.2197C12.3603 36.079 12.5511 36 12.75 36H21V32.25C21 32.0511 21.079 31.8603 21.2197 31.7197C21.3603 31.579 21.5511 31.5 21.75 31.5H30V27.75C30 27.5511 30.079 27.3603 30.2197 27.2197C30.3603 27.079 30.5511 27 30.75 27H38.25C38.4489 27 38.6397 27.079 38.7803 27.2197C38.921 27.3603 39 27.5511 39 27.75ZM44.25 3.375H40.5V2.25C40.5 2.05109 40.421 1.86032 40.2803 1.71967C40.1397 1.57902 39.9489 1.5 39.75 1.5H29.25C29.0511 1.5 28.8603 1.57902 28.7197 1.71967C28.579 1.86032 28.5 2.05109 28.5 2.25V3.375H24.75C24.4516 3.375 24.1655 3.49353 23.9545 3.7045C23.7435 3.91548 23.625 4.20163 23.625 4.5C23.625 9.2235 25.6125 11.8185 29.484 12.279C30.3033 13.5235 31.5568 14.4182 33 14.7885V19.5C32.2044 19.5 31.4413 19.8161 30.8787 20.3787C30.3161 20.9413 30 21.7044 30 22.5V24H39V22.5C39 21.7044 38.6839 20.9413 38.1213 20.3787C37.5587 19.8161 36.7956 19.5 36 19.5V14.7885C37.4435 14.4187 38.6972 13.5239 39.516 12.279C43.3875 11.8185 45.375 9.2235 45.375 4.5C45.375 4.20163 45.2565 3.91548 45.0455 3.7045C44.8345 3.49353 44.5484 3.375 44.25 3.375ZM25.9215 5.625H28.5V9C28.5 9.2805 28.545 9.5475 28.5825 9.8175C27.249 9.366 26.1555 8.2755 25.9215 5.625ZM38.19 6.9975L36.5625 8.583L36.9465 10.8225C36.956 10.8777 36.9498 10.9344 36.9288 10.9862C36.9077 11.0381 36.8726 11.083 36.8273 11.1159C36.7821 11.1488 36.7285 11.1684 36.6727 11.1725C36.6169 11.1766 36.5611 11.165 36.5115 11.139L34.5 10.083L32.4885 11.1405C32.4389 11.1665 32.3831 11.1781 32.3273 11.174C32.2715 11.1699 32.2179 11.1503 32.1727 11.1174C32.1274 11.0845 32.0923 11.0396 32.0712 10.9877C32.0502 10.9359 32.044 10.8792 32.0535 10.824L32.4375 8.5845L30.81 6.9975C30.77 6.9584 30.7417 6.90889 30.7283 6.85456C30.7149 6.80022 30.717 6.74323 30.7344 6.69003C30.7517 6.63682 30.7835 6.58952 30.8263 6.55346C30.8691 6.51741 30.9211 6.49404 30.9765 6.486L33.225 6.159L34.2315 4.1205C34.2562 4.07018 34.2946 4.0278 34.3421 3.99816C34.3897 3.96852 34.4447 3.9528 34.5007 3.9528C34.5568 3.9528 34.6118 3.96852 34.6594 3.99816C34.7069 4.0278 34.7453 4.07018 34.77 4.1205L35.7765 6.159L38.025 6.486C38.0803 6.49427 38.1321 6.51781 38.1747 6.55395C38.2173 6.5901 38.2489 6.63742 38.2661 6.69059C38.2832 6.74376 38.2852 6.80066 38.2718 6.85488C38.2583 6.90911 38.23 6.9585 38.19 6.9975ZM40.4175 9.8175C40.455 9.5475 40.5 9.2805 40.5 9V5.625H43.0785C42.843 8.2755 41.751 9.366 40.4175 9.8175Z" />
                <path fill="#f0578a"
                  d="M22.488 12.0015C22.5395 12.3957 22.4324 12.7942 22.1903 13.1095C21.9481 13.4248 21.5907 13.6311 21.1965 13.683L15.909 14.3775L14.3925 23.478L17.1885 24.9165C17.4331 25.0429 17.6382 25.2341 17.7814 25.4694C17.9245 25.7046 18.0002 25.9746 18 26.25V33C18 33.3978 17.842 33.7793 17.5607 34.0606C17.2794 34.3419 16.8978 34.5 16.5 34.5C16.1022 34.5 15.7206 34.3419 15.4393 34.0606C15.158 33.7793 15 33.3978 15 33V27.165L9.4755 24.321C8.92173 24.0356 8.47053 23.5849 8.18453 23.0315C7.89853 22.478 7.79192 21.8493 7.8795 21.2325L8.736 15.3795C8.23952 15.5105 7.78549 15.768 7.41822 16.1269C7.05095 16.4857 6.783 16.9337 6.6405 17.427L5.9445 19.9035C5.82378 20.2708 5.56604 20.5773 5.22496 20.7593C4.88388 20.9413 4.48574 20.9847 4.11344 20.8805C3.74114 20.7764 3.42337 20.5326 3.22631 20.2C3.02924 19.8674 2.96806 19.4716 3.0555 19.095L3.7515 16.6185C4.06843 15.4873 4.71089 14.4743 5.59899 13.7054C6.4871 12.9366 7.58165 12.4457 8.7465 12.294L20.805 10.71C21.0004 10.6839 21.199 10.6966 21.3894 10.7474C21.5799 10.7982 21.7584 10.8862 21.9148 11.0062C22.0711 11.1262 22.2023 11.2759 22.3006 11.4467C22.399 11.6175 22.4627 11.806 22.488 12.0015Z" />
                <path fill="#f0578a"
                  d="M12.7995 28.5675L10.437 36.4335C10.3222 36.8146 10.0608 37.1345 9.71011 37.3228C9.35947 37.5112 8.94837 37.5525 8.56725 37.4377C8.18614 37.3229 7.86622 37.0615 7.67789 36.7108C7.48956 36.3602 7.44823 35.9491 7.563 35.568L10.086 27.168L12.7995 28.5675Z" />
              </svg>

            </div>
            <div class="description mt-4">Tập trung kinh doanh và sự nghiệp mà vẫn
              <span class="aver-semi-bold">đầu tư hiệu quả</span>
            </div>
          </div>

          <div class="reason-item ">
            <div class="icon-container">

              <svg width="45%" height="45%" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path fill="#f0578a"
                  d="M36.3648 12.6188H4.31999L4.78079 9.64758C4.85859 9.14479 5.13286 8.69348 5.5433 8.39285C5.95374 8.09222 6.46677 7.96688 6.96959 8.04438L36.3648 12.6188ZM36 25.8188C35.3381 25.8188 34.8 26.3573 34.8 27.0188C34.8 27.6802 35.3381 28.2188 36 28.2188C36.6619 28.2188 37.2 27.6802 37.2 27.0188C37.2 26.3573 36.6619 25.8188 36 25.8188ZM45.6 15.9788V38.0588C45.6 38.568 45.3977 39.0563 45.0376 39.4164C44.6776 39.7765 44.1892 39.9788 43.68 39.9788H4.31999C3.81078 39.9788 3.32242 39.7765 2.96235 39.4164C2.60228 39.0563 2.39999 38.568 2.39999 38.0588V15.9788C2.39999 15.4696 2.60228 14.9812 2.96235 14.6211C3.32242 14.2611 3.81078 14.0588 4.31999 14.0588H43.68C44.1892 14.0588 44.6776 14.2611 45.0376 14.6211C45.3977 14.9812 45.6 15.4696 45.6 15.9788ZM42.48 20.7788C42.48 20.5878 42.4041 20.4047 42.2691 20.2697C42.1341 20.1346 41.9509 20.0588 41.76 20.0588C41.1873 20.0581 40.6383 19.8304 40.2333 19.4254C39.8284 19.0205 39.6006 18.4714 39.6 17.8988C39.6 17.7078 39.5241 17.5247 39.3891 17.3897C39.2541 17.2546 39.0709 17.1788 38.88 17.1788H9.11999C8.92904 17.1788 8.7459 17.2546 8.61088 17.3897C8.47585 17.5247 8.39999 17.7078 8.39999 17.8988C8.39999 19.0897 7.43087 20.0588 6.23999 20.0588C6.04904 20.0588 5.8659 20.1346 5.73088 20.2697C5.59585 20.4047 5.51999 20.5878 5.51999 20.7788V33.2588C5.51999 33.4497 5.59585 33.6329 5.73088 33.7679C5.8659 33.9029 6.04904 33.9788 6.23999 33.9788C7.43087 33.9788 8.39999 34.9479 8.39999 36.1388C8.39999 36.3297 8.47585 36.5129 8.61088 36.6479C8.7459 36.7829 8.92904 36.8588 9.11999 36.8588H38.88C39.0709 36.8588 39.2541 36.7829 39.3891 36.6479C39.5241 36.5129 39.6 36.3297 39.6 36.1388C39.6 34.9479 40.5691 33.9788 41.76 33.9788C41.9509 33.9788 42.1341 33.9029 42.2691 33.7679C42.4041 33.6329 42.48 33.4497 42.48 33.2588V20.7788ZM12 25.8188C11.3386 25.8188 10.8 26.3573 10.8 27.0188C10.8 27.6802 11.3386 28.2188 12 28.2188C12.6614 28.2188 13.2 27.6802 13.2 27.0188C13.2 26.3573 12.6614 25.8188 12 25.8188ZM30 27.0188C30 30.3274 27.3086 33.0188 24 33.0188C20.6914 33.0188 18 30.3274 18 27.0188C18 23.7101 20.6914 21.0188 24 21.0188C27.3086 21.0188 30 23.7101 30 27.0188ZM23.0352 25.6153V25.3383C23.0352 25.0383 23.279 24.7945 23.579 24.7945H24.4214C24.721 24.7945 24.9653 25.0383 24.9653 25.3383C24.9653 25.5292 25.0411 25.7124 25.1762 25.8474C25.3112 25.9824 25.4943 26.0583 25.6853 26.0583C25.8762 26.0583 26.0594 25.9824 26.1944 25.8474C26.3294 25.7124 26.4053 25.5292 26.4053 25.3383C26.4053 24.3466 25.6714 23.5301 24.7205 23.3847V22.873C24.7205 22.6821 24.6446 22.4989 24.5096 22.3639C24.3746 22.2289 24.1914 22.153 24.0005 22.153C23.8095 22.153 23.6264 22.2289 23.4914 22.3639C23.3563 22.4989 23.2805 22.6821 23.2805 22.873V23.3847C22.3282 23.5301 21.5947 24.3466 21.5947 25.3383V25.6153C21.5947 26.5273 22.213 27.3183 23.0976 27.5396L24.553 27.9034C24.7958 27.9644 24.9653 28.1809 24.9653 28.4314V28.7079C24.9653 29.0079 24.7214 29.2522 24.4214 29.2522H23.579C23.5076 29.2522 23.4368 29.2381 23.3707 29.2108C23.3047 29.1834 23.2447 29.1433 23.1941 29.0928C23.1436 29.0422 23.1035 28.9822 23.0761 28.9162C23.0488 28.8502 23.0347 28.7794 23.0347 28.7079C23.0347 28.5169 22.9589 28.3338 22.8238 28.1988C22.6888 28.0638 22.5057 27.9879 22.3147 27.9879C22.1238 27.9879 21.9406 28.0638 21.8056 28.1988C21.6706 28.3338 21.5947 28.5169 21.5947 28.7079C21.5947 29.7001 22.3286 30.5165 23.28 30.6615V31.2361C23.28 31.427 23.3558 31.6101 23.4909 31.7452C23.6259 31.8802 23.809 31.9561 24 31.9561C24.1909 31.9561 24.3741 31.8802 24.5091 31.7452C24.6441 31.6101 24.72 31.427 24.72 31.2361V30.662C25.6714 30.5165 26.4048 29.7001 26.4048 28.7084V28.4309C26.4048 27.5189 25.7875 26.7279 24.9024 26.5066L23.447 26.1428C23.3291 26.1136 23.2245 26.0457 23.1497 25.95C23.075 25.8542 23.0345 25.7362 23.0347 25.6148L23.0352 25.6153ZM41.04 21.4263V32.6113C40.3487 32.7537 39.7144 33.0956 39.2153 33.5946C38.7163 34.0937 38.3744 34.728 38.232 35.4193H9.76799C9.62562 34.728 9.28377 34.0936 8.78471 33.5945C8.28565 33.0955 7.65126 32.7536 6.95999 32.6113V21.4263C7.6512 21.284 8.28554 20.9422 8.78459 20.4432C9.28365 19.9442 9.62554 19.31 9.76799 18.6188H38.232C38.3744 19.31 38.7163 19.9444 39.2153 20.4434C39.7144 20.9425 40.3487 21.2839 41.04 21.4263ZM14.64 27.0188C14.64 25.5629 13.4558 24.3788 12 24.3788C10.5442 24.3788 9.35999 25.5629 9.35999 27.0188C9.35999 28.4746 10.5442 29.6588 12 29.6588C13.4558 29.6588 14.64 28.4746 14.64 27.0188ZM31.44 27.0188C31.44 22.9162 28.1026 19.5788 24 19.5788C19.8974 19.5788 16.56 22.9162 16.56 27.0188C16.56 31.1213 19.8974 34.4588 24 34.4588C28.1026 34.4588 31.44 31.1213 31.44 27.0188ZM38.64 27.0188C38.64 25.5629 37.4554 24.3788 36 24.3788C34.5446 24.3788 33.36 25.5629 33.36 27.0188C33.36 28.4746 34.5446 29.6588 36 29.6588C37.4554 29.6588 38.64 28.4746 38.64 27.0188Z" />
              </svg>
            </div>
            <div class="description mt-4">Tham gia với mức đầu tư thấp <span class="aver-semi-bold">chỉ từ
                10.000.000đ</span></div>
          </div>
        </div>
      </div>
    </div>

    <!-- Consultant section -->
    <div id="consultant_section" class="section-scroll-margin">
      <div class="consultant_container p-120 m-side-100 d-flex justify-content-evenly align-items-center">
        <div class="img-section" v-if="!props.mobileView">
          <img src="../assets/images/Model 2.png" alt="" class="block w-100">
        </div>

        <div class="detail-section">
          <div class="intro-container">
            <div class="intro-title aver-semi-bold fs-2">Kênh Đầu tư Vietnam Tourist</div>
            <div class="title-section aver-bold page-text-gradient">Cơ hội siêu hấp dẫn cho <br>Nhà đầu tư</div>
          </div>

          <div class="img-section_mobile" v-if="props.mobileView">
            <img src="../assets/images/Model 2.png" alt="" class="block w-100">
          </div>

          <div class="description-text mt-3 aver-regular">Kênh đầu tư Vietnam Tourist là quỹ
            đầu tư được thành lập bởi Công ty Cổ phần Thương mại và Dịch vụ Vietnam Tourist được thành lập năm 2017,
            là một trong những doanh nghiệp lữ hành hàng đầu tại Việt Nam với mạng lưới chi nhánh trên toàn quốc, chuyên
            tổ chức tour trong nước, quốc tế</div>

          <div class="btn-container">
            <button type="button" class="page-btn" data-bs-toggle="modal" data-bs-target="#staticBackdrop">Đăng ký tư vấn</button>
            <button type="button" class="ceo-mail--btn aver-semi-bold" data-bs-toggle="modal" data-bs-target="#backdropLetter">Thư ngỏ từ CEO</button>
          </div>
        </div>
      </div>
    </div>

    <!-- Benefit section -->
    <div id="benefit_section" class="section-scroll-margin">
      <div class="benefit_container p-120">
        <div class="title-section page-text-gradient text-center aver-bold mb-5">Ưu điểm khi đầu tư Vietnam Tourist
        </div>

        <div class="table-container w-100">
          <table class="table mx-auto">
            <thead>
              <tr>
                <th scope="col"></th>
                <th scope="col" class="economic-title_col fs-5 aver-semi-bold">Gửi tiết kiệm thông thường</th>
                <th scope="col" class="investment-title_col page-gradient-pink text-white fs-4 aver-bold"> Đầu tư vào
                  quỹ Vietnam Tourist
                </th>
              </tr>
            </thead>

            <tbody>
              <tr v-for="(item, index) in data" :key="index">
                <th scope="row" class="compare_row fs-5 aver-semi-bold">{{ item.title }}</th>
                <td class="economic-item aver-regular">{{ item.economicDetail }}</td>
                <td class="investment-item page-gradient-pink text-white aver-semi-bold">{{ item.invesmentDetail }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- Privilege section -->
    <div id="privilege_section" class="page-gradient-blue section-scroll-margin">
      <div class="privilege_container p-120 m-side-100">
        <div class="title-section text-white aver-bold text-center">Đặc quyền dành riêng cho cổ đông</div>

        <div class="privilege-item_container d-flex text-center text-white">
          <div class="privilege-item">
            <div class="icon-wrapper">
              <svg width="48%" height="48%" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path fill="#f0578a"
                  d="M3.75607 31.8032L1.01857 14.0102C0.816075 12.6962 2.31307 11.7993 3.37657 12.5973L11.9056 18.9933C12.1273 19.1593 12.3805 19.2785 12.6498 19.3434C12.919 19.4084 13.1987 19.4178 13.4718 19.371C13.7448 19.3243 14.0054 19.2224 14.2378 19.0716C14.4701 18.9207 14.6693 18.7241 14.8231 18.4937L21.9241 7.84375C22.6741 6.71875 24.3271 6.71875 25.0771 7.84375L32.1781 18.4937C32.3319 18.7241 32.5311 18.9207 32.7634 19.0716C32.9957 19.2224 33.2564 19.3243 33.5294 19.371C33.8024 19.4178 34.0821 19.4084 34.3514 19.3434C34.6207 19.2785 34.8739 19.1593 35.0956 18.9933L43.6246 12.5973C44.6896 11.7993 46.1851 12.6962 45.9826 14.0102L43.2451 31.8032H3.75607ZM41.1856 41.6763H5.81557C5.54512 41.6763 5.27731 41.623 5.02744 41.5195C4.77757 41.416 4.55053 41.2643 4.35929 41.073C3.97306 40.6868 3.75607 40.163 3.75607 39.6168V35.0942H43.2451V39.6168C43.2451 40.7538 42.3226 41.6763 41.1856 41.6763Z" />
              </svg>
            </div>
            <div class="desc-wrapper">
              <div class="title-privilege aver-bold fs-5">Chính sách đặc biệt khi mua Tour</div>
              <div class="desc-privilege aver-regular">Cổ đông trở thành khách VIP, nhận ngay ưu đãi đặc biệt trên mọi
                chuyến đi.</div>
            </div>
          </div>

          <div class="privilege-item">
            <div class="icon-wrapper">
              <svg width="48%" height="48%" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                <g clip-path="url(#clip0_187_11280)">
                  <path fill="#f0578a"
                    d="M47.9915 16H0V18C0 19.0609 0.421427 20.0783 1.17157 20.8284C1.92172 21.5786 2.93913 22 4 22H10C11.0609 22 12.0783 21.5786 12.8284 20.8284C13.5786 20.0783 14 19.0609 14 18C14 19.0609 14.4214 20.0783 15.1716 20.8284C15.9217 21.5786 16.9391 22 18 22H30C31.0609 22 32.0783 21.5786 32.8284 20.8284C33.5786 20.0783 34 19.0609 34 18C34 19.0609 34.4214 20.0783 35.1716 20.8284C35.9217 21.5786 36.9391 22 38 22H44C45.0609 22 46.0783 21.5786 46.8284 20.8284C47.5786 20.0783 48 19.0609 48 18V16H47.9915ZM47.5085 14L43.923 1.45C43.8035 1.03221 43.5512 0.664713 43.2042 0.403094C42.8573 0.141476 42.4345 -2.42327e-05 42 3.11275e-09H32.8395L35.6395 14H47.5085ZM15.1605 3.11275e-09H6C5.56546 -2.42327e-05 5.14273 0.141476 4.79577 0.403094C4.44881 0.664713 4.1965 1.03221 4.077 1.45L0.4915 14H12.3605L15.1605 3.11275e-09ZM28.7605 3.11275e-09H19.2395L16.4395 14H31.5605L28.7605 3.11275e-09ZM38 24C36.5232 24.0012 35.0983 23.4557 34 22.4685C32.9017 23.4557 31.4768 24.0012 30 24H18C16.5232 24.0012 15.0983 23.4557 14 22.4685C12.9017 23.4557 11.4768 24.0012 10 24H4C3.31822 23.9986 2.64175 23.8802 2 23.65V46C2 46.5304 2.21071 47.0391 2.58579 47.4142C2.96086 47.7893 3.46957 48 4 48H8V30C8 29.4696 8.21071 28.9609 8.58579 28.5858C8.96086 28.2107 9.46957 28 10 28H20C20.5304 28 21.0391 28.2107 21.4142 28.5858C21.7893 28.9609 22 29.4696 22 30V48H44C44.5304 48 45.0391 47.7893 45.4142 47.4142C45.7893 47.0391 46 46.5304 46 46V23.65C45.3583 23.8802 44.6818 23.9986 44 24H38ZM40 36C40 36.5304 39.7893 37.0391 39.4142 37.4142C39.0391 37.7893 38.5304 38 38 38H28C27.4696 38 26.9609 37.7893 26.5858 37.4142C26.2107 37.0391 26 36.5304 26 36V30C26 29.4696 26.2107 28.9609 26.5858 28.5858C26.9609 28.2107 27.4696 28 28 28H38C38.5304 28 39.0391 28.2107 39.4142 28.5858C39.7893 28.9609 40 29.4696 40 30V36Z" />
                </g>
                <defs>
                  <clipPath id="clip0_187_11280">
                    <rect width="100%" height="100%" fill="white" />
                  </clipPath>
                </defs>
              </svg>
            </div>
            <div class="desc-wrapper">
              <div class="title-privilege aver-bold fs-5">Cơ hội trở thành Đại lý bán hàng</div>
              <div class="desc-privilege aver-regular">Mức hoa hồng hấp dẫn, được đào tạo kỹ năng chuyên nghiệp - bài
                bản.
              </div>
            </div>
          </div>

          <div class="privilege-item">
            <div class="icon-wrapper">
              <svg width="48%" height="48%" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path fill="#f0578a"
                  d="M46.5926 28.6875C47.2734 28.6875 47.9978 28.1734 47.9993 27.2205L48 24.4688L47.9993 21.717C47.9978 20.7641 47.2734 20.25 46.5926 20.25C45.8243 20.25 45.1933 19.6245 45.1864 18.8562C45.1843 18.6704 45.2192 18.4861 45.2892 18.314C45.3592 18.1419 45.4628 17.9854 45.594 17.8538C45.7244 17.7215 45.8799 17.6166 46.0514 17.5451C46.2229 17.4736 46.4069 17.437 46.5926 17.4375C47.2734 17.4375 47.9978 16.9234 47.9993 15.9705L48 13.2188L47.9993 10.467C47.9978 9.51413 47.2734 9 46.5926 9H37.875C38.6517 9 39.2812 9.62953 39.2812 10.4062V13.2188C39.2812 13.9955 38.6517 14.625 37.875 14.625C37.0983 14.625 36.4688 13.9955 36.4688 13.2188V10.4062C36.4688 9.62953 37.0983 9 37.875 9H1.40738C0.726562 9 0.00215625 9.51413 0.00075 10.467L0 13.2188L0.00075 15.9705C0.00215625 16.9234 0.726562 17.4375 1.40738 17.4375C1.78491 17.4375 2.13975 17.5854 2.406 17.8538C2.53711 17.9855 2.64066 18.1419 2.71059 18.314C2.78052 18.4861 2.81542 18.6705 2.81325 18.8562C2.80669 19.6245 2.17566 20.25 1.40738 20.25C0.726562 20.25 0.00215625 20.7641 0.00075 21.717L0 24.4688L0.00075 27.2205C0.00215625 28.1734 0.726562 28.6875 1.40738 28.6875C2.17566 28.6875 2.80669 29.313 2.81325 30.0813C2.81542 30.267 2.78052 30.4514 2.71059 30.6235C2.64066 30.7956 2.53711 30.952 2.406 31.0837C2.27558 31.216 2.12009 31.3209 1.94862 31.3924C1.77715 31.4639 1.59315 31.5005 1.40738 31.5C0.726562 31.5 0.00215625 32.0141 0.00075 32.967L0 35.7188L0.00075 38.4705C0.00215625 39.4234 0.726562 39.9375 1.40738 39.9375H37.875C37.0983 39.9375 36.4688 39.308 36.4688 38.5312V35.7188C36.4688 34.942 37.0983 34.3125 37.875 34.3125C38.6517 34.3125 39.2812 34.942 39.2812 35.7188V38.5312C39.2812 39.308 38.6517 39.9375 37.875 39.9375H46.5926C47.2734 39.9375 47.9978 39.4234 47.9993 38.4705L48 35.7188L47.9993 32.967C47.9978 32.0141 47.2734 31.5 46.5926 31.5C46.4069 31.5005 46.2229 31.4639 46.0514 31.3924C45.8799 31.3209 45.7244 31.216 45.594 31.0837C45.4628 30.9521 45.3592 30.7956 45.2892 30.6235C45.2192 30.4514 45.1843 30.2671 45.1864 30.0813C45.1933 29.313 45.8243 28.6875 46.5926 28.6875ZM30.4629 24.5149L27.7719 27.138L28.4074 30.8422C28.5893 31.905 28.1605 32.9593 27.2882 33.5929C26.8082 33.9432 26.229 34.1314 25.6348 34.1301C25.1789 34.1296 24.73 34.0188 24.3263 33.8071L21 32.0581L17.6738 33.8071C17.2694 34.0207 16.8192 34.1326 16.3619 34.1331C15.7815 34.1331 15.2047 33.9514 14.7118 33.5933C13.8391 32.9593 13.4106 31.9054 13.5926 30.8422L14.2281 27.1385L11.5368 24.5149C10.7644 23.7623 10.4919 22.6575 10.8252 21.6321C11.158 20.6067 12.0282 19.8728 13.0954 19.7179L16.8145 19.1774L18.4779 15.8075C18.9551 14.8403 19.9215 14.2398 21 14.2398C22.0781 14.2398 23.0446 14.8403 23.5217 15.8071L25.1851 19.1774L28.9043 19.7179C29.9718 19.8731 30.8416 20.6066 31.1749 21.6321C31.5082 22.6575 31.2356 23.7623 30.4629 24.5149ZM39.2812 30.0938C39.2812 30.8705 38.6517 31.5 37.875 31.5C37.0983 31.5 36.4688 30.8705 36.4688 30.0938V27.2812C36.4688 26.5045 37.0983 25.875 37.875 25.875C38.6517 25.875 39.2812 26.5045 39.2812 27.2812V30.0938ZM39.2812 21.6562C39.2812 22.433 38.6517 23.0625 37.875 23.0625C37.0983 23.0625 36.4688 22.433 36.4688 21.6562V18.8438C36.4688 18.067 37.0983 17.4375 37.875 17.4375C38.6517 17.4375 39.2812 18.067 39.2812 18.8438V21.6562Z" />
                <path fill="#f0578a"
                  d="M21 17.0519L18.6822 21.7478L13.5 22.5011L17.25 26.1562L16.3649 31.3176L21 28.8808L25.6351 31.3176H25.6355L24.75 26.1562L28.5 22.5011L23.3178 21.7478L21 17.0519Z" />
              </svg>
            </div>
            <div class="desc-wrapper">
              <div class="title-privilege aver-bold fs-5">Tặng vé du lịch miễn phí 100%</div>
              <div class="desc-privilege aver-regular">Trải nghiệm những chuyến du lịch miễn phí
                hoàn toàn từ Vietnam Tourist.</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Growth section -->
    <div id="growth_section">
      <div class="growth_container d-flex justify-content-center align-items-end m-side-100">

        <div class="img-section" v-if="!props.mobileView">
          <img src="../assets/images/Model 3 copy.png" alt="" class="w-100 block">
        </div>

        <div class="detail-section p-120">
          <div class="title-section aver-bold page-text-gradient">Giá trị đầu tư tăng gấp <br> 3-30 lần/năm</div>

          <div class="img-section w-25 my-3" v-if="props.mobileView">
            <img src="../assets/images/Model 3 copy.png" alt="" class="w-100 block">
          </div>

          <div class="description-text mt-3">Vietnam Tourist cam kết minh bạch
            tài chính với báo cáo chi tiết hàng quý và từng năm, đảm bảo mục tiêu phát triển rõ ràng.
            Đồng hành cùng chúng tôi để gia tăng tài sản bền vừng!
          </div>

          <div class="btn-container">
            <button type="button" class="page-btn" data-bs-toggle="modal" data-bs-target="#staticBackdrop">Đăng ký tư vấn</button>
          </div>
        </div>

      </div>
    </div>

    <!-- Representative section -->
    <div id="representative_section">
      <div class="representative_container p-120 d-flex align-items-center justify-content-center">
        <div class="commit_container">
          <div class="intro-title aver-semi-bold fs-2 page-text-gradient-pink">Với niềm đam mê khát khao phát triển
            trong ngành du
            lịch</div>

          <div class="commit-text aver-semi-bold">Vietnam Tourist cam kết luôn đồng hành và
            tạo nên giá trị cùng quý cổ đông</div>

          <hr style="margin: 32px 0;" v-if="!mobileView">
          <hr style="margin: 16px 0;" v-if="mobileView">

          <div class="ceo_container d-flex align-items-center">
            <div class="ceo_wrapper">
              <p class="ceo-name aver-semi-bold page-text-gradient fs-4 m-0">Phạm Anh Nhân</p>
              <p class="ceo-position m-0">CEO of Vietnam Tourist</p>
            </div>

            <div class="btn-container" v-if="!mobileView">
              <button type="button" class="page-btn" data-bs-toggle="modal" data-bs-target="#staticBackdrop">Đăng ký tư vấn</button>
            </div>
          </div>
        </div>

        <div class="ceo-portrait text-center position-relative">
          <img src="../assets/images/ceo.jpg" alt="" class="w-100 block ">

          <div class="quote-container fs-1 position-absolute" v-if="!mobileView">
            <svg width="120" height="120" viewBox="0 0 120 120" fill="none" xmlns="http://www.w3.org/2000/svg">
              <circle cx="60" cy="60" r="60" fill="url(#paint0_linear_189_11420)" />
              <path
                d="M82.07 79.1996H63.51C61.6967 73.333 60.79 67.253 60.79 60.9596C60.79 54.5596 62.4433 49.493 65.75 45.7596C69.1633 41.9196 74.1767 39.9996 80.79 39.9996V48.9596C75.4567 48.9596 72.79 52.213 72.79 58.7196V61.7596H82.07V79.1996ZM55.03 79.1996H36.47C34.6567 73.333 33.75 67.253 33.75 60.9596C33.75 54.5596 35.4033 49.493 38.71 45.7596C42.1233 41.9196 47.1367 39.9996 53.75 39.9996V48.9596C48.4167 48.9596 45.75 52.213 45.75 58.7196V61.7596H55.03V79.1996Z"
                fill="white" />
              <defs>
                <linearGradient id="paint0_linear_189_11420" x1="60" y1="0" x2="60" y2="120"
                  gradientUnits="userSpaceOnUse">
                  <stop stop-color="#0082DF" />
                  <stop offset="1" stop-color="#005EA0" />
                </linearGradient>
              </defs>
            </svg>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.title-section {
  font-size: 48px;
  color: #005ea0;
}

.page-btn {
  padding: 16px 32px;
  font-size: 20px;
}

.section-scroll-margin {
  scroll-margin-top: 80px;
}

/* Form register section */
#form-register_section {
  height: 85vh;
  background-image: url(../assets/images/Banner.png);
  background-size: 100% 100%;
  background-repeat: no-repeat;
  background-position: left center;

  & .form-register_container {
    width: 40%;
    max-width: 600px;
    background-color: #fff;
    border-radius: 10px;

    & .container {
      padding: 32px;
    }

    & .input-investor {
      padding: 16px;
      border: 2px solid #d9d9d9;
      border-radius: 16px;
    }

    & select.input-investor {
      font-weight: 500;
    }

    & .input-investor::placeholder {
      font-size: 14px;
      font-family: 'AvertaSemibold', sans-serif !important;
      color: #d9d9d9;
    }

    & .page-btn {
      font-size: 18px;
      padding: 12px 24px;
    }
  }
}

/* Reason section */
#reason_section {

  & .reason_container {

    & .title-section {
      margin-bottom: 52px;
    }
  }

  & .icon-container {
    width: 80px;
    height: 80px;
    margin: auto;
    background-color: #feeff4;
    border: 2px solid #0181de;
    border-radius: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  & .reason-item {
    max-width: 270px;
  }
}

/* consultant_section */
#consultant_section {
  background-color: #f1f9ff;

  & .consultant_container {

    & .img-section {
      width: 35%
    }

    & .detail-section {
      width: 45%;

      & .intro-title {
        color: #f05083;
      }

      & .description-text {
        text-align: justify;
        font-size: 18px;
      }
    }

    & .ceo-mail--btn {
      padding: 16px 32px;
      margin-left: 20px;
      font-size: 20px;
      border: 2px solid transparent;
      background: linear-gradient(#f1f9ff, #f1f9ff) padding-box, linear-gradient(#0082df, #005ea0) border-box;
      border-radius: 15px;
      color: #005ea0;
      background-color: transparent;
    }

    & .ceo-mail--btn:hover {
      color: #f05083;
    }
  }

  & .btn-container {
    margin-top: 40px;
  }
}

/* Benefit section */
#benefit_section {

  & table {
    width: 80%;

    & tbody tr:last-child {
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

    & .economic-title_col {
      padding: 24px 32px;
      min-width: 400px;
    }

    & .investment-title_col {
      padding: 16px 40px;
      border-radius: 25px 25px 0 0;
    }

    & .compare_row {
      padding: 20px 32px;
    }

    & .economic-item {
      font-size: 18px;
      padding: 24px 32px;
    }

    & .investment-item {
      font-size: 18px;
      padding: 24px 40px;
    }
  }
}

#privilege_section {

  & .privilege_container {

    & .title-section {
      margin-bottom: 48px;
    }
  }

  & .icon-wrapper {
    width: 100px;
    height: 100px;
    margin: auto;
    background-color: #fff;
    border-radius: 25px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  & .desc-wrapper {
    margin-top: 28px;

    & .desc-privilege {
      font-size: 18px;
      margin-top: 12px;
    }
  }

  .privilege-item {
    padding: 0 32px;
  }
}

#growth_section {
  background-color: #f1f9ff !important;
  position: relative;

  & .growth_container {
    min-height: 550px;

    & .img-section {
      max-width: 382px;
    }

    & .detail-section {
      margin-left: 150px;
      width: 40%;
    }

    & .description-text {
      text-align: justify;
      font-size: 18px;
    }

    & .btn-container {
      margin-top: 20px;

      & .page-btn {
        padding: 16px 32px;
        font-size: 20px;
      }
    }
  }


}

#growth_section::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: url(../assets/images/bg-growth.png);
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  backdrop-filter: blur(5px);
  filter: blur(5px);
  opacity: 0.1;
  z-index: -1;
}

/* Representation section */
#representative_section {

  & .commit_container {
    width: 35%;
    margin-right: 120px;

    & .commit-text {
      font-size: 48px;
      margin-top: 20px;
      line-height: 1.3;
    }

    & .btn-container {
      margin-left: 40px;
    }
  }

  .ceo_container {

    & .ceo-position {
      font-size: 18px;
      color: #808080;
    }
  }

  & .ceo-portrait img {
    border-radius: 64px;
    min-height: 600px;
    max-width: 500px;
    object-fit: cover;
  }

  & .quote-container {
    bottom: 40%;
    left: -12%;
  }
}


@media (max-width: 1024px) {

  .title-section {
    font-size: 28px;
    margin-bottom: 32px;
    text-align: center;
  }

  .page-btn {
    font-size: 16px !important;
    padding: 12px 24px;
    margin-top: 12px;
  }

  #form-register_section {
    height: fit-content;
    background: none !important;

    & .form-register_wrapper {
      height: fit-content;
      padding: 40px 0;
      margin: 0 16px;
      border-bottom: 1px solid #d9d9d9;
    }

    & .form-register_container {
      width: 100%;
      margin: auto;

      & .container {
        padding: 0;
      }

      & .register-item_wrapper {
        margin-bottom: 0 !important;
      }

      & .register-item {
        width: 100%;
        display: flex;
        flex-direction: column;
        margin-bottom: 12px !important;
      }
    }
  }


  #reason_section {
    margin: 40px 16px 80px;

    & .reason_container {
      padding: 0;
    }

    & .reason-item_container {
      flex-wrap: wrap;
      text-align: start !important;

      & .reason-item {
        width: 50%;
        max-width: 171px;

        & .icon-container {
          width: 52px;
          height: 52px;
          margin: 0;
        }

        & .description {
          margin-top: 12px !important;
          font-size: 14px;
        }
      }

      & .reason-item:nth-child(1),
      .reason-item:nth-child(3) {
        margin-right: 16px;
      }

      & .reason-item:nth-child(3),
      .reason-item:nth-child(4) {
        margin-top: 32px;
      }
    }

  }

  #consultant_section .consultant_container {
    margin: 0 16px;
    padding: 80px 0;

    & .detail-section {
      width: 100%;
    }

    & .img-section_mobile {
      text-align: center;
      margin-bottom: 32px;

      & img {
        width: 80% !important;
      }
    }

    & .intro-container {
      text-align: center;

      & .intro-title {
        font-size: 18px;
      }
    }

    & .description-text {
      font-size: 14px !important;
    }

    & .btn-container {
      margin-top: 20px;
      display: flex;
      justify-content: center;

      & .page-btn {
        margin: 0;
      }

      & .ceo-mail--btn {
        padding: 12px 24px;
        margin-left: 16px;
        font-size: 16px !important;
      }
    }
  }

  #benefit_section {

    & .benefit_container {
      margin: 80px 16px;
      padding: 0;
    }

    & .table-container table {
      margin: 0;
      width: 100%;

      & thead th,
      tbody th,
      tbody td {
        min-width: 119px;
      }

      & thead th {
        font-size: 14px !important;
        padding: 16px 8px;
      }

      & tbody th {
        font-size: 12px !important;
        padding: 20px 8px;
      }

      & tbody td {
        font-size: 12px;
        padding: 24px 8px;
      }

      & tr th:last-child {
        font-size: 16px !important;
      }
    }
  }

  #privilege_section {

    & .privilege_container {
      padding: 80px 0;
      margin: 0 16px;
    }

    & .privilege-item_container {
      display: flex;
      flex-direction: column;

      & .privilege-item {
        display: flex;
        padding: 0;
        margin-bottom: 40px;

        & .icon-wrapper {
          width: 52px;
          min-width: 52px;
          height: 52px;
          border-radius: 15px;
          margin: 0;
        }

        & .desc-wrapper {
          text-align: left;
          margin-left: 20px;
          margin-top: 0;
        }

        & .title-privilege {
          font-size: 16px !important;
        }

        & .desc-privilege {
          font-size: 14px !important;
          width: 100%;
          margin: 0;
          padding-top: 8px;
        }
      }
    }
  }

  #growth_section {
    background-color: #f1f9ff;

    & .growth_container {
      padding: 80px 0;
      margin: 0 16px;

      & .img-section {
        width: 100% !important;
        text-align: center;
        margin: 24px auto !important;

        & img {
          width: 80% !important;
        }
      }

      & .detail-section {
        width: 100%;
        margin-left: 0;
        padding: 0;

        & .title-section {
          margin: auto;
        }

        & .description-text {
          font-size: 14px !important;
          margin-bottom: 24px;
        }

        & .btn-container {
          display: flex;
          justify-content: center;
          margin: 0;

          & button {
            margin: 0;
          }
        }
      }
    }
  }

  #growth_section::before {
    background: none !important;
  }

  #representative_section .representative_container {
    padding: 80px 0;
    margin: 0 16px;
    flex-direction: row-reverse;
    align-items: start !important;

    & .commit_container {
      margin-right: 0;
      margin-left: 24px;
      width: 60%;

      & .intro-title {
        font-size: 14px !important;
      }

      & .commit-text {
        font-size: 20px;
        margin-top: 12px;
      }

      & .ceo_container {
        & .ceo-name {
          font-size: 14px !important;
        }

        & .ceo-position {
          font-size: 12px !important;
        }
      }
    }

    & .ceo-portrait {
      width: 40% !important;

      & img {
        min-height: 159px !important;
        min-width: 128px !important;
        border-radius: 24px;
        object-fit: cover;
      }


    }
  }
}
</style>
