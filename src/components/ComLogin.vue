<template>
    <div>
      <h2>Đăng nhập</h2>
      <input  placeholder="Tên đăng nhập" />
      <input  type="password" placeholder="Mật khẩu" />
      <button >Đăng nhập</button>
      <p >báo lỗi</p>
    </div>
  </template>
  
  <script>
  
  export default {
    name:"ComLogin",
    data() {
      return {
        username: '',
        password: '',
        error: '',
        
      };
    },
    
  };
  </script>
  