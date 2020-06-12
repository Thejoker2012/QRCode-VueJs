<template>
    <div class="home">
        <h1>{{title}}</h1>
        <div>
            <input type="text" size="25"
                   placeholder="Digite para gerar..."
                   v-model="text"
            >
        </div>
        <div v-if="text" class="output">
            <img :src="newQrcode" alt="QRCode">
        </div>
    </div>
</template>

<script>
    // @ is an alias to /src
    import QRious from 'qrious';

    export default {
        name: 'Home',
        data() {
            return {
                title: 'Gerador de QrCode',
                text: 'https://www.google.com.br',
                qrcode: new QRious({size: 300})

            }
        },
        computed: {
            newQrcode() {
                this.qrcode.value = this.text
                return this.qrcode.toDataURL()
            }
        },
        methods: {

        }

    }
</script>

<style>

    h1{
        color: white;
    }

    div.home{
        background: #2c3e50;
        height: 100vh;
    }

    div.output {

        height: 400px;
        width: auto;

    }

    div img{
        background: white;
        margin: 10px;
        border: 5px solid white;
    }

</style>
