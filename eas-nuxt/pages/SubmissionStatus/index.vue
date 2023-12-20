<template>
    <div class="container">
        <form @submit.prevent="submitForm" class="form">
            <label for="email">Check Email Kamu Disini</label>
            <input v-model="email" type="text" id="email" name="email" placeholder="EmailAnda@gmail.com" required>
            <button type="submit">Check</button>
        </form>
    </div>
</template>

<style>
    .container {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh; 
    }

    .form {
        text-align: center;
        padding: 20px;
        border: 1px solid #ccc;
        border-radius: 8px;
        background-color: #f9f9f9;
        max-width: 400px; 
        width: 100%; 
    }
    label {
        display: block;
        margin-bottom: 10px;
    }

    input,
    button {
        margin-bottom: 10px;
        padding: 8px;
        border-radius: 5px;
        border: 1px solid #ccc;
    }

    button {
        background-color: #007bff;
        color: white;
        border: none;
        cursor: pointer;
    }

    button:hover {
        background-color: #0056b3;
    }
</style>

<script setup>
const router = useRouter();
const email = ref('');
const submitForm = () => {
    router.push(`/submissionStatus/${email.value}`);
}
</script>
<style lang="">
</style>