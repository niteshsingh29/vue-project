<script>
export default {
    name: "Form",

}
</script>


<template>
    <div class="form">
        <p>Message is: {{ message }}</p>
        <input v-model="message" placeholder="edit me" />

        <input type="checkbox" id="checkbox" v-model="checked" />
        <label for="checkbox">{{ checked }}</label>
    </div>
</template>


<style scoped>
* {
    margin: 0;
    padding: 0;
    color: red;
    font-size: medium;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.form-group {
    margin: 10px;
}
</style>
