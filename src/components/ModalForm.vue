<script setup>
import { reactive, ref } from 'vue';

const props = defineProps({
    mobileView: {
        type: Boolean,
        required: true
    },
    cleanedProvincesData: {
        type: Array,
        required: true
    },
    form: {
        type: Object
    }
})

const localForm = reactive(props.form)


// Emit sự kiện để thông báo lên parent
const emit = defineEmits(['submit-form']);

let isLoading = ref(false)

const handleSubmit = async () => {
    isLoading.value = true;
    console.log(props.form)

    await emit('submit-form', props.form); // Gửi dữ liệu lên parent
    isLoading.value = false;
}

const moneyList = [10000000, 20000000, 30000000, 50000000, 100000000, 200000000, 500000000, 1000000000]


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
                                <button type="button" class="btn-close" data-bs-dismiss="modal"
                                    aria-label="Close"></button>
                            </div>

                            <div class="title aver-semi-bold fs-3 mb-3">👉 <span class="page-text-gradient">Đăng ký nhận
                                    tư vấn đầu tư!</span>
                            </div>

                            <form method="post" @submit.prevent="handleSubmit">
                                <!-- Name input -->
                                <div class="register-item mb-3">
                                    <label for="nameInput" class="form-label aver-semi-bold">Họ và tên
                                        <span class="page-text-gradient-pink">(*)</span></label>
                                    <input required type="text" class="form-control input-investor" id="nameInput"
                                        v-model="localForm.name" placeholder="Nhập Họ và tên của bạn"
                                        @input="event => text = event.target.value">
                                </div>

                                <!-- phone and email input -->
                                <div class="register-item_wrapper mb-3 row">
                                    <div class="register-item col-6">
                                        <label for="phoneInput" class="form-label aver-semi-bold">Số điện thoại
                                            <span class="page-text-gradient-pink">(*)</span></label>
                                        <input required type="number" class="form-control input-investor"
                                            id="phoneInput" v-model.number="localForm.phone"
                                            placeholder="Nhập số điện thoại của bạn"
                                            @input="event => text = event.target.value">
                                    </div>
                                    <div class="register-item col-6">
                                        <label for="emailInput" class="form-label aver-semi-bold">Email
                                            <span class="page-text-gradient-pink">(*)</span></label>
                                        <input required type="email" class="form-control input-investor" id="emailInput"
                                            v-model="localForm.email" placeholder="Nhập email của bạn"
                                            @input="event => text = event.target.value">
                                    </div>
                                </div>

                                <!-- investment -->
                                <div class="register-item mb-3">
                                    <label for="investmentInput" class="form-label aver-semi-bold">Số tiền dự định
                                        đầu tư
                                        <span class="page-text-gradient-pink">(*)</span></label>
                                    <select name="investmentInput" id="investmentInput"
                                        class="form-select form-select-sm input-investor aver-semi-bold"
                                        v-model="localForm.investment">
                                        <option disabled>Chọn số tiền dự định đầu tư</option>
                                        <option v-for="(money, index) in moneyList" :key="index">{{
                                            money.toLocaleString() }} đ</option>
                                    </select>
                                </div>

                                <!-- city -->
                                <div class="register-item mb-4">
                                    <label for="cityInput" class="form-label aver-semi-bold">Tỉnh/Thành phố</label>
                                    <select name="cityInput" id="cityInput"
                                        class="form-select form-select-sm input-investor aver-semi-bold"
                                        v-model="localForm.provinces">
                                        <option disabled>Chọn Tỉnh/Thành phố</option>
                                        <option v-for="(item, index) in cleanedProvincesData" :key="index">{{ item }}
                                        </option>
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

    & .modal-header,
    .modal-body {
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
        font-size: 14px;
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

@media (max-width: 500px) {

    .modal {
        background: linear-gradient(rgba(0, 130, 223, 0.3), rgba(0, 94, 160, 0.3));
    }

    .modal-dialog {
        width: 90% !important;
        max-width: inherit;
        margin: auto;
    }

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

        & .title {
            font-size: 20px !important;
        }

        & label {
            font-size: 14px;
        }

        & .register-item_wrapper {
            flex-direction: column;

            & .register-item {
                width: 100% !important;
            }
        }

        & .input-investor, 
            select.input-investor, 
            .input-investor::placeholder {
            font-size: 12px;
        }
    }

    .page-btn {
        font-size: 16px !important;
    }
}
</style>