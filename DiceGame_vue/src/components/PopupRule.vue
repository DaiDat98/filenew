<template>
    <div class="wrapper-popup" v-bind:class="getClassPopup">
        <div class="rule">
            <h3>Luật chơi</h3>
            <p>isPlaying: true <br>
score -> Có 2 điểm chính thức hành cho 2 người chơi <br>
dice1 - dice2 <br>
    activePlayer: 1 -> Người thứ nhất đang chơi <br>
    activePlayer: 2 -> Người thứ hai đang chơi
<br>
NewGame  <br>
    1. Show Popup <br>
    2. Reset Data  <br>
    3. Xay dựng Popup  <br>
<br>
Roll Dice  <br>
    1. Random dư liệu 2 con xúc xắc  <br>
    2. Kiểm tra xem người dùng có xoay đúng con số 1 không?  <br>
        2.1. Nếu xoay trúng số 1 -> Đổi lượt chơi -> Reset điểm tạm thời  <br>
        2.2. Nếu xoay ok -> Cộng dồn vào điểm tạm thời cho người chơi đó.  <br>
<br>
Hold -> Lấy điểm  <br> 
    1. So sánh xem điểm cuối cùng lớn hơn FinalScore???  <br>
    2. Chưa đủ điểm -> Cộng dồn 'ĐIỂM CHÍNH THỨC' => Đổi lượt chơi <br>
</p>
<b>copyright by datdat_cd18tt5 <br> </b>

            <button 
                v-on:click="confirm"
                class="confirm">Đã hiểu</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'popup-rule',
    props: {
        isOpenPopup: { type: Boolean, default: false }
    },
    data() {
        return {

        }
    },
    methods: {
        confirm() {
            // Truyền event ra App.vue
            console.log('confirm PopupRule.vue');
            this.$emit('handleConfirm')
        }
    },
    computed: {
        getClassPopup: function() {
            return {
                'open-popup': this.isOpenPopup
            }
        }
    }
}
</script>

<style>
    .wrapper-popup {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background-color: rgba(0,0,0,0.4);
        opacity: 0;
        visibility: hidden;
        transition: all .3s ease;
    }
    .wrapper-popup.open-popup {
        opacity: 1;
        visibility: visible;
    }
    .rule {
        width: 350px;
        padding: 20px;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%) scale(1.2);
        background-color: #fff;
        position: absolute;
        font-family: Arial, Helvetica, sans-serif;
        transition: all .3s ease;
    }
    .open-popup .rule {
        transform: translate(-50%, -50%) scale(1);
    }
    /* scale -> class */
    .rule h3 {
        margin-bottom: 10px;
    }
    .rule .confirm {
        cursor: pointer;
        margin-top: 20px;
        padding: 8px 15px;
        border: 2px solid #333;
        background-color: #fff;
        transition: all .3s ease;
    }
    .rule .confirm:hover {
        color: #fff;
        background-color: #333;
    }
    /* kết hợp CSS3 với VueJs để xây dựng hiệu ứng - Zoom in - Zoom out */
</style>
