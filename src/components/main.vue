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

    <!-- Formulario -->
    <Modal :header="true" @close="showModal = false" v-if="showModal">
        <template #title v-if="showMessage"> Datos de contacto </template>
        <template #content>
            <ContactForm 
                @setShowMessage="onSetMessage"
                ref="form"
            />
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
import ContactForm from './Modal/Form.vue'

export default {
    components:{Modal, ContactForm},
    setup() {
        let showModal   = ref(false)
        let email       = ref('')
        let apellido    = ref('')
        let nombre      = ref('')
        let telefono    = ref('')
        let showMessage     = ref(true)
        return {
            showModal,
            email,
            apellido,
            nombre,
            telefono,
            showMessage
        }
    },
    methods:{
        onSetMessage(value){
            this.showMessage = value
        }
    }
}
</script>