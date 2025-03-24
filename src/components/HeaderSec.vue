<template>
    <div class="header-section">
        <h5 class="header-title">Chat</h5>
        <div class="images-container">
            <img src="@/assets/home.svg" alt="Home" class="header-image"> /
            <img src="@/assets/chat.svg" alt="Chat" class="header-image">
        </div>
    </div>
  </template>
  
  <style scoped>
  /* تصميم الهيدر */
  .header-section {
    width: 100%;
    max-width: 1050px; /* يجعل الحجم مرنًا حسب الشاشة */
    height: 49px;
    background-color: #ffffff;
    border-radius: 10px;
    margin: 20px auto; /* توسيط العنصر */
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 8px 20px;
  }
  
  /* ترتيب العنوان */
  .header-title {
    font-size: 16px;
    color: #333;
  }
  
  /* ترتيب الأيقونات */
  .images-container {
    display: flex;
    align-items: center;
    gap: 10px;
  }
  
  /* تصميم الأيقونات */
  .header-image {
    width: 25px;
    height: 20px;
    cursor: pointer;
    transition: transform 0.3s ease-in-out;
  }
  
  .header-image:hover {
    transform: scale(1.1);
  }
  
  /* جعل التصميم متجاوبًا */
  @media (max-width: 768px) {
    .header-section {
    flex-direction: column;
    height: auto;
    text-align: center;
    padding-top: 0 !important;
    padding-bottom: 0 !important;
    padding-right: 0 !important;  /* المساحة من اليمين */
    padding-left: 0 !important;   /* المساحة من اليسار */
}

  
    .images-container {
      margin-top: 10px;
      justify-content: center;
    }
  }

  </style>
  