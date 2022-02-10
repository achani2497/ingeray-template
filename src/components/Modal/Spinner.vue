<template>
    <div class="spinner-container">
        <div class="hollow-dots-spinner">
            <div class="dot"></div>
            <div class="dot"></div>
            <div class="dot"></div>
        </div>
        <div class="text">
            Enviando mail
        </div>
    </div>
</template>
<style scoped>
    .spinner-container{
      height: 300px;
      width: 100%;
      display: flex;
      flex-direction: column;
      gap: 1rem;
      color: white;
      font-size: 20px;
      justify-content: center;
      align-items: center;
      margin-top: -2rem;
    }
    .hollow-dots-spinner .dot {
      width: 20px;
      height: 20px;
      margin: 0 calc(15px / 2);
      border: calc(15px / 5) solid var(--dark-lilac);
      border-radius: 50%;
      float: left;
      transform: scale(0);
      animation: hollow-dots-spinner-animation 1500ms ease infinite 0ms;
    }

    .hollow-dots-spinner .dot:nth-child(1) {
      animation-delay: calc(300ms * 1);
    }

    .hollow-dots-spinner .dot:nth-child(2) {
      animation-delay: calc(300ms * 2);
    }

    .hollow-dots-spinner .dot:nth-child(3) {
      animation-delay: calc(300ms * 3);

    }

    @keyframes hollow-dots-spinner-animation {
      50% {
        transform: scale(1);
        opacity: 1;
      }
      100% {
        opacity: 0;
      }
    }
</style>