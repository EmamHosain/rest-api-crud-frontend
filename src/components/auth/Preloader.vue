<script setup>

const props = defineProps({
    isLoading: Boolean
})

</script>
<template>
    <div class="hossain">
        <div class="load" v-if="isLoading">
            <hr />
            <hr />
            <hr />
            <hr />
        </div>
    </div>
</template>


<style scoped>
body {
    background: #ECF0F1;
    position: relative;

}

.hossain {
    width: 100%;
    min-height: 100vh;
  
}

.load {
    position: absolute;
    top: 50%;
    left: 50%;
    z-index: 100;
    transform: translate(-50%, -50%);
    width: 100px;
    height: 100px;
}


.load hr {
    border: 0;
    margin: 0;
    width: 40%;
    height: 40%;
    position: absolute;
    border-radius: 50%;
    animation: spin 2s ease infinite;
}

.load :first-child {
    background: #19A68C;
    animation-delay: -1.5s;
}

.load :nth-child(2) {
    background: #F63D3A;
    animation-delay: -1s;
}

.load :nth-child(3) {
    background: #FDA543;
    animation-delay: -0.5s;
}

.load :last-child {
    background: #193B48;
}

@keyframes spin {

    0%,
    100% {
        transform: translate(0);
    }

    25% {
        transform: translate(160%);
    }

    50% {
        transform: translate(160%, 160%);
    }

    75% {
        transform: translate(0, 160%);
    }
}
</style>