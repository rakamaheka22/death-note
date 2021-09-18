<template>
  <header>
    <img src="/images/death-note.png" alt="Logo Death Note">
  </header>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style scoped>
header {
    display: flex;
    align-items: center;
    justify-content: center; 
}

img {
    margin-top: 50px;
}

@media only screen and (max-width: 600px) {
    header {
        margin-left: 24px;
        margin-right: 24px;
    }
    img {
        margin-top: 24px;
        width: 100%;
    }
}
</style>
