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
        <template #title v-if="!enviado && !fallido"> Datos de contacto </template>
        <template #content>
            <form ref="form" @submit.prevent="enviarMail()" class="form flex column" v-if="!enviado &&!loading && !fallido">
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
                    <label class="title" for="telefono">Whatsapp</label>
                    <input type="text" id="telefono" name="telefono" v-model="telefono">
                </div>
                <button type="submit">Enviar datos</button>
            </form>
            <Spinner v-else-if="loading && (!enviado || !fallido)" />
            <div class="message-wrapp" v-else>
                <div class="message success flex column" v-if="enviado">
                    <div class="check-container">
                        <div class="check"></div>
                    </div>
                    Enviado! Gracias por comunicarte
                </div>
                <div class="message failed flex column" v-if="fallido">
                    <div class="check-container">
                        <div class="stick" id="stick1"></div>
                        <div class="stick" id="stick2"></div>
                    </div>
                    Hubo un error al tratar de enviar el mail.
                    Por favor comunicate llamando a alguno de nuestros telefonos
                </div>
            </div>
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
    box-shadow: 0px 1px 1px rgba(0, 0, 0, .04),
                0px 2px 2px rgba(0, 0, 0, .08),
                0px 4px 4px rgba(0, 0, 0, .12),
                0px 8px 8px rgba(0, 0, 0, .16),
                0px 16px 16px rgba(0, 0, 0, .2);
    transition: all .3s ease-in-out;
}
.button:hover{
    cursor: pointer;
    box-shadow: none;
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
    padding-left: 5px;
    padding-top: 5px;
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

.message{
    gap: 2rem;
    padding: 1rem;
    height: 200px;
    width: 100%;
    margin-top: -2rem;
    color: white;
    justify-content: center;
    align-items: center;
    text-align: center;
    font-size: 20px;
    animation: fadeIn .6s ease-in forwards;
}
.success{
    background-color: hsl(120, 39%, 54%);
}
.check-container{
    border: 2px solid white;
    height: 60px;
    width: 60px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 100px;
}
.check{
  display: inline-block;
  transform: rotate(45deg);
  height: 27px;
  width: 12px;
  border-bottom: 2px solid white;
  border-right: 2px solid white;
}
.stick{
    width: 1px;
    height: 40px;
    border: 1px solid white;
}
#stick1{
    transform: rotate(45deg);
}
#stick2{
    transform: rotate(-45deg);
}
.failed{
    background-color: hsl(0, 100%, 67%);
}

@keyframes grow{
    from{
        width: 0%
    }
    to{
        width: 75%
    }
}

@keyframes fadeIn{
    from{
        opacity: 0;
    }
    to{
        opacity: 100%;
    }
}

</style>
<script>
import {ref} from 'vue'
import Modal from './Modal/Modal.vue'
import emailjs from '@emailjs/browser'
import Spinner from './Modal/Spinner.vue'

export default {
    components:{Modal, Spinner},
    setup() {
        let showModal   = ref(false)
        let email       = ref('')
        let apellido    = ref('')
        let nombre      = ref('')
        let telefono    = ref('')
        let loading     = ref(false)
        let enviado     = ref(false)
        let fallido     = ref(false)
        return {
            showModal,
            email,
            apellido,
            nombre,
            telefono,
            loading,
            enviado,
            fallido
        }
    },
    methods:{
        enviarMail(){
            this.loading = true
            emailjs.sendForm('service_ng4qgtq', 'template_6oqv2pr', this.$refs.form, 'user_eeVYemHTnHjSJqpAxC8wh')
                .then(response => {
                    console.log(response.text)
                    this.loading = false
                    this.enviado = true
                })
                .catch(e => {
                    this.loading = false
                    this.fallido = true
                    console.log(e.text)
                })
        }
    }
}
</script>