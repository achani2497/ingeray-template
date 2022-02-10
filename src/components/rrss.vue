<template>
    <div class="rrss-container">
        <div class="seccion" id="seccion1">
            <div class="title t-22"> Quiénes somos </div>
            <p>
                Inge Ray SRL es una empresa argentina creada en 1992 y desde entonces nos comprometimos y dedicamos a brindar Soluciones Tecnológicas para la Salud que permitan a nuestros clientes ofrecer una medicina de calidad.
            </p>
        </div>
        <div class="seccion" id="seccion2">
            <div class="title t-22"> Contactos </div>
            <div class="telefonos flex wrap">
                <div class="telefono">
                    <div class="title t-19">DIVISIÓN HUMANOS</div>
                    <span>ventasingeray@gmail.com</span>
                    <span>+54 9 11 3851-0695</span>
                </div>
                <div class="telefono">
                    <div class="title t-19">SERVICIO TÉCNICO</div>
                    <span>serviciotecnico@ingeray.com.ar</span>
                    <span>+54 9 11 4192-6162</span>
                </div>
                <div class="telefono">
                    <div class="title t-19">DIVISIÓN VETERINARIA</div>
                    <span>ventas@ingeray.com.ar</span>
                    <span>+54 9 11 5976-7596</span>
                </div>
                <div class="telefono">
                    <div class="title t-19">ATENCIÓN COMERCIAL</div>
                    <span>ingeraysrl@gmail.com</span>
                    <span>+54 9 11 4192-6163</span>
                </div>
            </div>
        </div>
        <div class="seccion" id="seccion3">
            <div class="title t-22"> Redes Sociales </div>
            <div class="iconos flex">
                <a href="https://www.facebook.com/IngeRayVET" target="_blank" ref="noopener noreferrer">
                    <div class="icon facebook"></div>
                </a> 
                <a href="https://www.instagram.com/p/CMK8U71DnXq/" target="_blank" ref="noopener noreferrer">
                    <div class="icon instagram"></div>
                </a> 
                <a href="https://www.youtube.com/channel/UCmPvf69gHGonIM2fglmhBig" target="_blank" ref="noopener noreferrer">
                    <div class="icon youtube"></div>
                </a> 
            </div>
        </div>
        <a class="icon whatsapp" href="https://wa.me/5491149604301" target="_blank" ref="noopener noreferrer"></a>
    </div>
</template>
<style scoped>
.rrss-container{
    display: flex;
    position: relative;
    background-color: var(--dark-lilac);
    color: white;
    padding: 1rem;
    flex-direction: column;
    gap: 2rem;
    text-align: center;
    font-size: 17px;
}
.seccion{
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: .7rem;
}
.t-22{
    font-size: 20px;
}
.t-19{
    font-size: 17px;
}
.telefonos{
    gap: 1rem;
    justify-content: center;
}
.telefono{
    display: flex;
    flex-direction: column;
    gap: .3rem;
}
.iconos{
    justify-content: space-around;
    width: 100%;
    max-width: 250px;
}
.icon{
    height: 60px;
    width: 60px;
    background-position: center;
    background-repeat: no-repeat;
    background-size: 105%;
}
.facebook{
    background-image: url('~@/assets/images/rrss/facebook.svg');
}
.instagram{
    background-image: url('~@/assets/images/rrss/instagram.svg');
}
.youtube{
    background-image: url('~@/assets/images/rrss/youtube.svg');
}
.whatsapp{
    position: absolute;
    height: 90px;
    width: 90px;
    border-radius: 100px;
    right: 30px;
    top: -50px;
    background-image: url('~@/assets/images/rrss/whatsapp.svg');
    background-repeat: no-repeat;
    background-size: contain;
    background-position: center;
}
@media screen and (min-width: 541px) {
    .telefonos{
        justify-content: space-around;
    }
    .telefono{
        width: 48%;
        margin: 0 auto;
    }
}
@media screen and (min-width: 769px){
    .rrss-container{
        display: grid;
        grid-template-columns: 38% 62%;
        grid-template-areas: 
        "col1 col2"
        "col3 col3";
        width: 100%;
        text-align: start;
        gap: 0;
        row-gap: 1rem;
    }
    .seccion{
        align-items: flex-start;
    }
    .telefonos{
        justify-content: flex-start;
        flex-direction: row;
        gap: 0;
        row-gap: 1rem;
    }
    .telefono{
        margin: 0;
        width: 47%;
    }
    #seccion3{
        grid-area: col3;
        align-items: center;
    }
}
@media screen and (min-width: 1024px){
    .rrss-container{
        grid-template-columns: 1fr 2fr .5fr;
        grid-template-areas: unset;
        padding: 2rem;
        gap: 2rem;
        justify-content: center;
    }
    .t-22{
        font-size: 18px;
    }
    .t-19{
        font-size: 15px;
    }
    #seccion2{
        justify-self: center;
        max-width: 450px;
    }
    .telefonos{
        justify-content: center;
    }
    .telefono{
        width: 50%;
    }
    #seccion3{
        grid-area: unset;
        align-items: flex-start;
    }
    .iconos{
        justify-content: space-between;
        max-width: 220px;
    }
}
@media screen and (min-width: 1150px) {
    .rrss-container{
        padding: 2rem 8rem;
    }
}
</style>