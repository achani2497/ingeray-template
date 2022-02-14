<template>
    <Form 
        @submit="onSubmit"
        :validation-schema="schema"
        @invalid-submit="onInvalidSubmit"
        class="form flex column"
        v-if="!enviado &&!loading && !fallido"
        ref="form"
    >
        <TextInput
            name="email"
            type="email"
            label="Mail"
            placeholder="email@example.com"
        />
        <TextInput
            name="apellido"
            type="text"
            label="Apellido"
            placeholder="Tu Apellido"
        />
        <TextInput
            name="nombre"
            type="text"
            label="Nombre"
            placeholder="Tu Nombre"
        />
        <TextInput
            name="telefono"
            type="text"
            label="Whatsapp"
            placeholder=""
        />
        <button type="submit" class="submit-btn">Enviar</button>
    </Form>
    <Spinner v-else-if="loading && (!enviado || !fallido)" />
    <div class="message-wrapp" v-else>
        <div class="message sent flex column" v-if="enviado">
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
<style scoped>
:root {
  --primary-color: #0071fe;
  --error-color: #f23648;
  --error-bg-color: #fddfe2;
  --success-color: #21a67a;
  --success-bg-color: #e0eee4;
}
.form{
    padding: 1rem;
    gap: 1rem;
    font-size: 20px;
    color: white;
}
.submit-btn{
    background-color: hsl(120, 39%, 54%);
    color: white;
    border: none;
    border: 1px solid hsl(120, 39%, 40%);
    border-radius: 25px;
    font-size: 20px;
    padding: .3rem 0;
    margin-top: 1rem;
    transition: transform .3s ease-in-out;
}
.submit-btn:hover{
    cursor: pointer;
}
.submit-btn.invalid {
  animation: shake 0.5s;
  animation-iteration-count: infinite;
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
    /* animation: fadeInInge .6s ease-in forwards; */
}
.sent{
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

@keyframes shake {
  0% {
    transform: translate(1px, 1px);
  }
  10% {
    transform: translate(-1px, -2px);
  }
  20% {
    transform: translate(-3px, 0px);
  }
  30% {
    transform: translate(3px, 2px);
  }
  40% {
    transform: translate(1px, -1px);
  }
  50% {
    transform: translate(-1px, 2px);
  }
  60% {
    transform: translate(-3px, 1px);
  }
  70% {
    transform: translate(3px, 1px);
  }
  80% {
    transform: translate(-1px, -1px);
  }
  90% {
    transform: translate(1px, 2px);
  }
  100% {
    transform: translate(1px, -2px);
  }
}
@keyframes fadeInInge {
    0%{
        opacity: 0;
    }
    100%{
        opacity: 100%;
    }
}
</style>
<script>
import {ref} from 'vue'
import {Form} from 'vee-validate'
import TextInput from './TextInput.vue'
import * as Yup from 'yup'
import Spinner from './Spinner.vue'
import emailjs from '@emailjs/browser'

export default {
    components:{Form, TextInput, Spinner},
    emits:['setShowMessage'],
    setup() {
        let loading     = ref(false)
        let enviado     = ref(false)
        let fallido     = ref(false)
        const schema = Yup.object().shape({
            nombre: Yup.string().required(),
            apellido: Yup.string().required(),
            email: Yup.string().email().required(),
            telefono: Yup.string().required().min(8)
        })
        return{
            schema,
            loading,
            enviado,
            fallido
        }
    },
    created(){
        emailjs.init('user_eeVYemHTnHjSJqpAxC8wh')
    },
    methods:{
        onSubmit(){
            this.loading = true
            let data = {
                service_id:'service_ng4qgtq',
                template_id:'template_6oqv2pr'
            }
            let template_params = {
                email:      document.getElementById('email').value,
                apellido:   document.getElementById('apellido').value,
                nombre:     document.getElementById('nombre').value,
                telefono:   document.getElementById('telefono').value
            }
            emailjs.send(data.service_id, data.template_id, template_params)
                .then(response => {
                    console.log(response.text)
                    this.loading = false
                    this.enviado = true
                    this.$emit('setShowMessage', false)
                })
                .catch(e => {
                    this.loading = false
                    this.fallido = true
                    this.$emit('setShowMessage', false)
                    console.log(e)
                })
        },
        onInvalidSubmit(){
            const submitBtn = document.querySelector(".submit-btn")
            submitBtn.classList.add('invalid')
            setTimeout(() => {
                submitBtn.classList.remove('invalid')
            }, 1000)
        }
    }
}
</script>