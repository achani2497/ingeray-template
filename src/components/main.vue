<template>
    <div class="main-container flex column">
        <img :src="require('@/assets/images/30Aniversary.svg')" alt="Imagen30Aniversario">
        <div class="text flex column">
            <h1 class="futura t-40">SITIO EN CONSTRUCCIÓN</h1>
            <p class="futura t-20">LA NUEVA WEB ESTARÁ LISTA MUY PRONTO</p>
        </div>
        <div class="loader flex column">
            <div class="loaded"></div>
            <div class="percentages flex">
                <div class="percentage-left">0%</div>
                <div class="percentage-right">100%</div>
            </div>
        </div>
        <button class="button" type="button" @click="showModal = true">
            Quiero que me avisen
        </button>
    </div>
    <Modal :header="true" @close="showModal = false" v-if="showModal">
        <template #title> Datos de contacto </template>
        <template #content>
            <form @submit.prevent="enviarMail()" class="form flex column">
                <div class="input-group">
                    <label class="title" for="email">Email</label>
                    <input type="text" id="email" name="email" v-model="email">
                </div>
                <div class="input-group">
                    <label class="title" for="apellido">Apellido</label>
                    <input type="text" id="apellido" name="apellido" v-model="apellido">
                </div>
                <div class="input-group">
                    <label class="title" for="nombre">Nombre</label>
                    <input type="text" id="nombre" name="nombre" v-model="nombre">
                </div>
                <div class="input-group">
                    <label class="title" for="whatsapp">Whatsapp</label>
                    <input type="text" id="whatsapp" name="whatsapp" v-model="whatsapp">
                </div>
                <button type="submit">Enviar datos</button>
            </form>
        </template>
    </Modal>
</template>
<style scoped>
.main-container{
    background-color: var(--lilac);
    align-items: center;
    text-align: center;
    padding: 4rem 1rem;
    gap: 2rem;
    color: white;
}
.t-40{
    font-size: 40px;
}
.t-20{
    font-size: 20px;
}
img{
    width: 100%;
    max-width: 350px;
}
.text{
    gap: 1rem;
    width: 100%;
    word-wrap: break-word;
}
.loader{
    width: 80%;
    max-width: 400px;
    gap: .5rem;
}
.loaded{
    width: 100%;
    height: 13px;
    position: relative;
    background: white;
}
.loaded::before{
    content: '';
    position: absolute;
    left: 0;
    width: 0%;
    height: 100%;
    background-color: var(--bluish-green);
    animation: grow 2s ease-in-out forwards
}
.percentages{
    justify-content: space-between;
}
.percentage-left{
    margin-left: -10px;
}
.percentage-right{
    margin-right: -20px;
}
.button{
    padding: 1rem;
    color: white;
    background-color: var(--bluish-green);
    border-radius: 10px;
    border: 2px solid gray;
    font-weight: bold;
    font-size: 16px;
}
.form{
    padding: 1rem;
    gap: 1rem;
    font-size: 20px;
    color: white;
}
.input-group{
    display: flex;
    flex-direction: column;
}
.input-group input{
    height: 30px;
    font-size: 20px;
    border: none;
    border-bottom: 1px solid white;
    background-color: transparent;
    color: rgb(244, 244, 244);
    transition: all .1s ease-in;
}
.input-group input:focus{
    outline: none;
    border-bottom: 2.5px solid white;
}
form button{
    background-color: hsl(120, 39%, 54%);
    color: white;
    border: none;
    border: 1px solid hsl(120, 39%, 40%);
    border-radius: 25px;
    font-size: 20px;
    padding: .3rem 0;
    margin-top: 1rem;
    z-index: 2;
}
form button:hover{
    cursor: pointer;
}
@keyframes grow{
    from{
        width: 0%
    }
    to{
        width: 75%
    }
}
</style>
<script>
import {ref} from 'vue'
import Modal from './Modal/Modal.vue'

export default {
    components:{Modal},
    setup() {
        let showModal   = ref(false)
        let email       = ref('')
        let apellido    = ref('')
        let nombre      = ref('')
        let whatsapp    = ref('')
        return {
            showModal,
            email,
            apellido,
            nombre,
            whatsapp
        }
    },
    methods:{
        enviarMail(){
            console.log(`Enviando mail a ${this.nombre} . . .`)
        }
    }
}
</script>