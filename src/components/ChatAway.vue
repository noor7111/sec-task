<template>
    <div class="away-header">
      <div class="user-info">
        <div class="avatar-container">
          <img src="@/assets/pic3.svg" alt="Logo" class="avatar" />
          <span class="status-dot"></span>
        </div>
        <span class="status-text">Away</span>
      </div>
  
      <div class="actions">
        <button class="action-btn">
          <img src="@/assets/no.svg" alt="Block" class="icon-imgm" style="background-color: white;">
        </button>
        <button class="action-btn">
          <img src="@/assets/trash.svg" alt="Delete" class="icon-imgl" style="background-color: white;">
        </button>
        <button class="action-btn">
          <img src="@/assets/tel.svg" alt="Call" class="icon-imggg" style="background-color: white ;">
        </button>
        <button class="action-btn">
          <img src="@/assets/ved.svg" alt="Video" class="icon-imgg" style="background-color: white;">
        </button>
        <button class="action-btn">
          <img src="@/assets/trio.svg" alt="More" class="icon-img" style="background-color: white;">
        </button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ChatAway'
  }
  </script>
  
  <style scoped>
  .away-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 12px 16px;
    background-color: white;
    border-bottom: 1px solid #eee;
    border-top-right-radius: 10px;
    
  }
  
  .user-info {
    display: flex;
    align-items: center;
    gap: 10px;
  }
  
  .avatar-container {
    position: relative;
  }
  
  .avatar {
    width: 35px;
    height: 35px;
    border-radius: 50%;
  }
  
  .status-dot {
    position: absolute;
    bottom: 2px;
    right: 2px;
    width: 7px;
    margin-left: 8px;
    margin-top: 8px;
    height: 7px;
    background-color: #36C76C;
    border-radius: 50%;
    border: 1px solid #36C76C;
  }
  
  .status-text {
    color: #666;
    font-size: 14px;
  }
  
  .actions {
    display: flex;
    align-items: center;
    gap: 10px;
  }
  
  .action-btn {
    background: none;
    border: none;
    padding: 5px;
    cursor: pointer;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 38px;
    height: 38px;
    transition: background 0.2s ease-in-out;
  }
  
 
  
  .icon-img {
    width: 22px;
    height: 22px;
    object-fit: contain;

  }

  .icon-imgg{
    width: 22px;
    height: 22px;
    object-fit: contain;
    margin-left: 30px;

  }

  .icon-imggg{
    width: 22px;
    height: 22px;
    object-fit: contain;
    margin-left: 60px;

  }

  .icon-imgl{
    width: 22px;
    height: 22px;
    object-fit: contain;
    margin-left: 55px;

  }

  .icon-imgm{
    width: 22px;
    height: 22px;
    object-fit: contain;
    margin-left: 70px;

  }
  
  /* Media Queries for responsiveness */
  @media (max-width: 768px) {
    .away-header {
      flex-direction: column;
      align-items: flex-start;
      gap: 10px;
      padding: 12px;
    }
  
    .user-info {
      margin-bottom: 10px;
    }
  
    .actions {
      justify-content: center;
      gap: 8px;
    }
  
    .action-btn {
      width: 35px;
      height: 35px;
    }
  
    .icon-img {
      width: 18px;
      height: 18px;
    }
  }
  
  @media (max-width: 480px) {
    .avatar {
      width: 30px;
      height: 30px;
    }
  
    .status-text {
      font-size: 12px;
    }
  
    .action-btn {
      width: 32px;
      height: 32px;
    }
  
    .icon-img {
      width: 16px;
      height: 16px;
    }
  }
  </style>
  