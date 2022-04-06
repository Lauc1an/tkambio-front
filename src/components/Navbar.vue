<script setup>
import Logo from '../icons/Logo.vue'
</script>

<template>
    <nav class="navbar">
        <Logo class="nav-logo" alt="TKambio Logo" />
    </nav>

</template>

<style lang="scss" scoped>
.navbar {
    padding-top: 19px;
    padding-bottom: 19px;
    display: flex;
    justify-content: center;
    background: #00adf4;
    box-shadow: 0 5px 4px 0 rgba(0, 0, 0, 0.24);
    background: -moz-linear-gradient(top, #00adf4 0%, #0073ec 100%);
    background: -webkit-gradient(left top, left bottom, color-stop(0%, #00adf4), color-stop(100%, #0073ec));
    background: -webkit-linear-gradient(top, #00adf4 0%, #0073ec 100%);
    background: -o-linear-gradient(top, #00adf4 0%, #0073ec 100%);
    background: -ms-linear-gradient(top, #00adf4 0%, #0073ec 100%);
    background: linear-gradient(to bottom, #00adf4 0%, #0073ec 100%);
    filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#00adf4', endColorstr='#0073ec', GradientType=0 );
    .nav-logo {
        width: 120px;
        height: auto;
    }
}

@media (min-width: 992px) {
    .navbar {
        .nav-logo {
            width: 180px;
        }
    }
}
</style>
