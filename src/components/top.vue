<template>
    <div class="top-container flex wrap">
        <div class="info flex">
            <div class="icon ubicacion"></div>
            <div class="text wrap">
                <span>Campillo 2585</span>
                <div class="separator">|</div> 
                <span>C1427DCC</span>
                <div class="separator">|</div> 
                <span>CABA</span>
                <div class="separator">|</div> 
                <span>ARGENTINA</span>
            </div>
        </div>
        <div class="info flex">
            <div class="icon telefono"></div>
            <div class="text wrap">
                <span>Lunes a Viernes de 8 a 17h.</span>
                <div class="separator">|</div> 
                <span>11 4523-5792 / 3999</span>
            </div>
        </div>
        <div class="info flex">
            <div class="icon mail"></div>
            <div class="text wrap">
                <span>administracion@ingeray.com.ar</span>
                <div class="separator">/</div>
                <span>ingeraysrl@gmail.com</span>
            </div>
        </div>
    </div>
</template>
<style scoped>
.top-container{
    justify-content: space-around;
    align-items: center;
    width: 100%;
    background-color: var(--dark-blue);
    min-height: 4rem;
    height: fit-content;
    color: white;
    padding: 1rem;
    gap: 1rem;
    font-size: 15px;
}
.info{
    align-items: center;
    gap: .7rem;
    letter-spacing: 2px;
}
.icon{
    height: 35px;
    width: 35px;
    background-size: 200%;
    background-position: center;
    background-repeat: no-repeat;
}
.info:nth-child(n+2) .icon{
    background-size: 160%;
}
.text{
    display: flex;
    gap: .3rem;
}
.ubicacion{
    background-image: url('~@/assets/images/NavIcons/inge_map.svg');
}
.telefono{
    background-image: url('~@/assets/images/NavIcons/inge_phone.svg');
}
.mail{
    background-image: url('~@/assets/images/NavIcons/inge_mail.svg');
}
@media screen and (min-width: 769px){
    .top-container{
        font-size: 12px;
        display: inline-flex;
    }
}
</style>