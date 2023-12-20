<template>
    <div class="container">
        <div class="content">
            Email ini: {{ accept.email }} statusnya sudah di {{ accept.status }}
        </div>
    </div>
</template>

<style>
    .container {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh; 
    }

    .content {
        text-align: center;
        padding: 20px;
        border: 1px solid #ccc;
        border-radius: 8px;
        background-color: #f9f9f9;
    }
</style>

<script setup>
const route = useRoute().params.email
const { data: request } = await useFetch('http://localhost:5000/api/submissions');
const submissions = request._rawValue.docs;

let accept;

submissions.forEach(submission => {
    console.log(submission.email);
    if (submission.email === route) {
        accept = submission;
    }
});

console.log(accept)
</script>