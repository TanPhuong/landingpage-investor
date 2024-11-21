<script setup>
import { reactive, toRaw } from 'vue';

const props = defineProps({
  mobileView: {
    type: Boolean,
    required: true
  },
  provincesData: {
    type: Array
  }
})

let formData = reactive({
  name: "",
  phone: "",
  email: "",
  investment: "Chọn số tiền dự định đầu tư",
  provinces: "Chọn Tỉnh/Thành phố"
})

const handleSubmit = (e) => {
  e.preventDefault() 
  console.log(toRaw(formData));
}


</script>

<template>
    <main>
        <div class="modal fade" id="staticBackdrop" data-bs-keyboard="false" tabindex="-1"
            aria-labelledby="staticBackdropLabel" aria-hidden="true">
            <div class="modal-dialog modal-dialog-centered">
                <div class="modal-content">
                    <div class="modal-body d-flex justify-content-around">
                            <div class="img-section w-50" v-if="!props.mobileView">
                                <img src="../assets/images/Pop-up.png" alt="" class="w-100 block">
                            </div>

                            <div class="form_container w-50">
                                <div class="d-flex justify-content-end">
                                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                                </div>

                                <div class="aver-semi-bold fs-3 mb-3">👉 <span class="page-text-gradient">Đăng ký nhận tư vấn đầu tư!</span>
                                </div>

                                <form method="post" @submit="handleSubmit">
                                    <!-- Name input -->
                                    <div class="register-item mb-3">
                                        <label for="nameInput" class="form-label aver-semi-bold">Họ và tên
                                            <span class="page-text-gradient-pink">(*)</span></label>
                                        <input required type="text" class="form-control input-investor" id="nameInput" v-model="formData.name"
                                            placeholder="Nhập Họ và tên của bạn" @input="event => text = event.target.value">
                                    </div>

                                    <!-- phone and email input -->
                                    <div class="register-item_wrapper mb-3 row">
                                        <div class="register-item col-6">
                                            <label for="phoneInput" class="form-label aver-semi-bold">Số điện thoại
                                                <span class="page-text-gradient-pink">(*)</span></label>
                                            <input required type="number" class="form-control input-investor" id="phoneInput" v-model.number="formData.phone"
                                                placeholder="Nhập số điện thoại của bạn" @input="event => text = event.target.value">
                                        </div>
                                        <div class="register-item col-6">
                                            <label for="emailInput" class="form-label aver-semi-bold">Email
                                                <span class="page-text-gradient-pink">(*)</span></label>
                                            <input required type="email" class="form-control input-investor" id="emailInput" v-model="formData.email"
                                                placeholder="Nhập email của bạn" @input="event => text = event.target.value">
                                        </div>
                                    </div>

                                    <!-- investment -->
                                    <div class="register-item mb-3">
                                        <label for="investmentInput" class="form-label aver-semi-bold">Số tiền dự định
                                            đầu tư
                                            <span class="page-text-gradient-pink">(*)</span></label>
                                        <select name="investmentInput" id="investmentInput"
                                            class="form-select form-select-sm input-investor aver-semi-bold" v-model="formData.investment">
                                            <option disabled>Chọn số tiền dự định đầu tư</option>
                                            <option>10,000,000</option>
                                            <option>20,000,000</option>
                                            <option>30,000,000</option>
                                            <option>50,000,000</option>
                                            <option>100,000,000</option>
                                            <option>200,000,000</option>
                                            <option>500,000,000</option>
                                            <option>1,000,000,000</option>
                                        </select>
                                    </div>

                                    <!-- city -->
                                    <div class="register-item mb-4">
                                        <label for="cityInput" class="form-label aver-semi-bold">Tỉnh/Thành phố
                                            <span class="page-text-gradient-pink">(*)</span></label>
                                        <select name="cityInput" id="cityInput"
                                            class="form-select form-select-sm input-investor aver-semi-bold" v-model="formData.provinces">
                                            <option disabled>Chọn Tỉnh/Thành phố</option>
                                            <option v-for="(item, index) in provincesData" :key="index">{{ item }}</option>
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
        </div>
    </main>
</template>

<style scoped>

.modal-dialog {
    max-width: max-content;

    & .modal-content {
        max-width: 1175px;
        padding: 32px; 
        border-radius: 32px;
    }

    & .modal-header {
        border-bottom: none;
    }

    & .modal-header, .modal-body {
        padding: 0;
    }
}

.img-section img {
    border-radius: 16px;
    height: -webkit-fill-available;
}

.form_container {
    width: 40%;
    max-width: 600px;
    background-color: #fff;
    border-radius: 10px;
    margin-left: 40px;

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

@media (max-width: 430px) {
    .modal-content {
        padding: 16px !important;
        border-radius: 16px !important;
    }

    .modal-body {
        display: block;
    }

    .form_container {
        width: 100% !important;
        margin-left: 0;
    }

    .page-btn {
        font-size: 16px !important;
    }
}


</style>