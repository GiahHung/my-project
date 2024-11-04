<template>
    <div>
      <h2>Đăng ký tài khoản</h2>
      <input  placeholder="Tên đăng nhập" />
      <input  type="password" placeholder="Mật khẩu" />
      <input
       
        type="password"
        placeholder="Xác nhận mật khẩu"
      />
      <button >Đăng ký</button>
      <p  class="error">báo lỗi</p>
      <p  class="success">báo thành công</p>
    </div>
  </template>
  
  <script>
  
  export default {
    data() {
      return {
        username: "",
        password: "",
        confirmPassword: "",
        error: "",
        success: "",
       
      };
    },
    
  };
  </script>
  
  <style>
  </style>