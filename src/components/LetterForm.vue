<script setup>
const props = defineProps({
    mobileView: {
        type: Boolean,
        required: true
    }
})
</script>

<template>
    <main>
        <div class="modal fade" id="backdropLetter" data-bs-keyboard="false" tabindex="-1"
            aria-labelledby="backdropLetterLabel" aria-hidden="true">
            <div class="modal-dialog modal-dialog-centered">
                <div class="modal-content">
                    <div class="d-flex justify-content-end">
                        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                    </div>
                    <div class="modal-body d-flex justify-content-around">
                        <div class="img-section w-50" v-if="!props.mobileView">
                            <img src="../assets/images/Pop-up.png" alt="" class="w-100 block">
                        </div>

                        <div class="letter_container w-50">

                            <div class="title aver-semi-bold mb-2">Kính gửi: Quý nhà đầu tư !</div>

                            <div class="paragraph mb-2">
                                Đầu tiên, Ban Giám Đốc <span class="aver-semi-bold">Công ty Cổ phần Thương mại và Dịch
                                    vụ Du Lịch Vietnam Tourist(Ten viết tắt: Vietnam Tourist)</span> xin được gửi đến
                                Quý nhà đầu tư lời chào trân trọng, lời chúc sức khoẻ và thành công!
                            </div>
                            <div class="paragraph-2 mb-2">
                                Vietnam Tourist tự hào là một trong những doanh nghiệp lữ hành uy tín, có kinh nghiệm tổ
                                chức các tour khách lẻ ghép đoàn khởi hành hàng tuần,
                                tour đoàn thể với số lượng lớn, vừa đi du lịch, vừa kết hợp hội nghị, hội thảo, teamm
                                building, mang đến sự trải nghiệm tuyệt vời và ấn tượng trong lòng khách hàng.
                            </div>
                            <div class="paragraph-3 mb-2">
                                Vietnam Tourist chuyên tổ chức các tour trong nước và quốc tế, tổ chức các loại hình du
                                lịch Mice, du lịch kết hợp Team Building từ cao cấp đến hoàn hảo nhất, du lịch sinh
                                thái, văn hoá, nghỉ dưỡng, hành hương,...
                                Ngoài ra, Công ty còn cung cấp các dịch vụ hỗ trợ khác như: Bán vé máy bay, vé tàu, tư
                                vấn Visa, hộ chiếu, đặt phòng khách sạn - resort, nhà hàng, du thuyền, cho thuê xe du
                                lịch...
                            </div>
                            <div class="paragraph-4 mb-2">
                                Vietnam Tourist là một đơn vị lữ hành tại Việt Nam được thành lập ngày 15/08/2017. Sau
                                hơn 7 năm thành lập, chúng tôi đã có những bước phát triển nhanh chóng, vượt bậc với 6
                                chi nhánh phân bổ đều ở các nơi là
                                <span class="aver-semi-bold"> Hà Nội, TP. Đồng Hới - Quảng Bình, TP. HCM, TP. Cần Thơ,
                                    TP. Cà Mau.</span>
                                Với phương châm không ngừng hoàn thiện trong thiết kế tour, đa dạng hoá các sản phẩm du
                                lịch, trong nhiều năm qua, Vietnam Tourist đã tổ chức được hàng ngàn chuyến tour du lịch
                                nội địa, tour inbound,
                                tour outbound hấp dẫn và chất lượng. Với mối quan hệ chặt chẽ và mật thiết với các nhà
                                cung cấp, Vietnam Tourist luôn đưa ra giá tour cạnh tranh, chất lượng đảm bảo luôn mang
                                đến sự hài lòng cho từng du khách.
                            </div>
                            <div class="paragraph-5 mb-2">
                                Với thiện chí hợp tác cùng phát triển, Vietnam Tourist xin gửi lời mời kêu gọi đầu tư
                                đến các Quý nhà đầu tư có nhu cầu quan tâm và mong muốn hợp tác cùng chúng tôi để cùng
                                thực hiện chung các hoạt động Đầu tư- Kinh doanh nhằm
                                gia tăng giá trị và lợi ích chung cho cả hai bên. Vietnam Tourist rất tin tưởng vào sự
                                thành công tốt đẹp và lâu dài trong quá trình hợp tác giữa chúng tôi và Quý nhà đầu tư.
                            </div>
                            <div class="end aver-semi-bold">Chúc Quý nhà đầu tư hạnh phúc và thành công!</div>
                        </div>
                    </div>
                </div>
            </div>

        </div>
    </main>
</template>

<style scoped>
::-webkit-scrollbar {
    display: none;
}

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
    max-height: 560px;
}

.letter_container {
    max-width: 600px;
    max-height: 560px;
    margin-left: 40px;
    font-size: 16px;
    overflow: scroll;
    text-align: justify;
}

@media (max-width: 430px) {
    .modal-content {
        padding: 16px !important;
        border-radius: 16px !important;
    }

    .modal-body {
        display: block;
    }

    .letter_container {
        width: 100% !important;
        margin-left: 0;
        padding: 0 8px;
    }

}
</style>
