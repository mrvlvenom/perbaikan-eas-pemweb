<template>
    <div class="button-container">
      <NuxtLink to="/submission"><button>Registrasi</button></NuxtLink>
      <NuxtLink to="/submissionstatus"><button>Check Status Email</button></NuxtLink>
    </div>
  </template>
  
  <style>
  .button-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background-image: url('https://images.pexels.com/photos/1335077/pexels-photo-1335077.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940');
    background-size: cover;
    background-position: center center;
    background-repeat: no-repeat;
    background-attachment: fixed;
  }
  
  button {
    margin: 5px;
    padding: 10px 20px;
    background-color: #3498db;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  </style>
  