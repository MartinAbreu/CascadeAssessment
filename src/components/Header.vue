<template>
    <div class="header">
        <div><img src="https://www.cascadefintech.com/wp-content/uploads/2018/04/Cascade-Logo_Primary-212.png" alt=""></div>
        <div></div>
    </div>
</template>

<script>
export default {
    name: 'Header'
}
</script>

<style scoped>
.header {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    margin-bottom: 40px;
}

</style>