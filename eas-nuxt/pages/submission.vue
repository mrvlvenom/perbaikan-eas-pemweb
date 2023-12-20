<template>
  <div class="container">
    <div class="form-container">
      <form @submit.prevent="submitForm" class="registration-form">
        <div class="form-group">
          <label for="name">Masukkan Nama Anda</label>
          <input v-model="formData.name" type="text" id="name" name="name" placeholder="Januar Eko" required>
        </div>
        <div class="form-group">
          <label for="email">Email</label>
          <input v-model="formData.email" type="email" id="email" name="email" placeholder="emailanda@gmail.com" required>
        </div>
        <div class="form-group">
          <label for="phone">Masukkan Nomor Anda</label>
          <input v-model="formData.phone" type="text" id="phone" name="phone" placeholder="081231456985" required>
        </div>
        <div class="form-group">
          <label for="school">Masukkan Nama Sekolah Anda</label>
          <input v-model="formData.school" type="text" id="school" name="school" placeholder="SMAN 1 Bangil" required>
        </div>
        <button type="submit">Register</button>
      </form>
      <div v-if="isFormSubmitted" class="success-message">
        <h1>Berhasil Registrasi</h1>
      </div>
    </div>
  </div>
</template>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(135deg, #fdfcfb, #e2e2e2);
  position: relative;
}

.form-container {
  width: 350px;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.1);
  background-color: #fff;
  transition: transform 0.3s ease-in-out;
}

.form-container:hover {
  transform: translateY(-5px);
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input[type="text"],
input[type="email"] {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 3px;
}

button {
  padding: 10px 15px;
  background-color: #3498db;
  color: white;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}

.success-message {
  margin-top: 20px;
  text-align: center;
  position: relative;
  width: 100%;
}

.success-message h2 {
  padding: 10px;
  background-color: #2ecc71;
  color: white;
  border-radius: 5px;
  box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.3);
  display: inline-block;
}
</style>

<script setup>
const formData = ref({
    name: '',
    email: '',
    phone: '',
    school: '',
});

const isFormSubmitted = ref(false);

const getCurrentDate = () => {
    var currentDate = new Date();

    var day = currentDate.getDate();
    var monthNames = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
    var month = monthNames[currentDate.getMonth()];
    var year = currentDate.getFullYear();

    var formattedDate = day + ' ' + month + ' ' + year;

    return formattedDate
}

const submitForm = async () => {
    console.log(getCurrentDate());
  try {
    const response = await fetch('http://localhost:5000/api/submissions', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      credentials: 'include',
      body: JSON.stringify({
        name: formData.value.name,
        email: formData.value.email,
        phone: formData.value.phone,
        school: formData.value.school,
        date: getCurrentDate()
      }),
    });

    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }

    const responseData = await response.json();
    console.log(responseData);
    isFormSubmitted.value = true;
    formData.value = {
      name: '',
      email: '',
      phone: '',
      school: '',
    };
  } catch (error) {
    console.error('Error submitting form:', error.message);
  }
};
</script>
