<template>
    <div class="container-main">
        <div class="grid">
            <slot/>
        </div>
    </div>
</template>

<style scoped>
.container-main {
    display: flex;
    justify-content: center;
    width: 100%;
}
.grid {
    width: 80%
}
</style>