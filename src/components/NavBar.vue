<template>
  <nav class="navbar navbar-expand-lg">
    <div class="container-fluid">
      <!-- زر القائمة عند تصغير الشاشة (نقلناه لليمين) -->
      <button class="navbar-toggler" type="button" @click="toggleMobileMenu">
        <img src="@/assets/trio.svg" alt="Menu" class="icon-img">
      </button>

      <!-- أزرار البحث والشبكة -->
      <div class="bottom-buttons" style="margin-left: 300px; margin-top: 20px;">
        <button class="btn">
          <img src="@/assets/ser.svg" alt="Search" class="icon-img">
        </button>
        <button class="btn">
          <img src="@/assets/seq.svg" alt="Grid" class="icon-img">
        </button>
      </div>

      <!-- عناصر الشريط العلوي -->
      <div class="top-bar" :class="{ 'show-mobile': isMobileMenuOpen }">
        <img src="@/assets/moon.svg" alt="Dark Mode" class="icon-img" @click="toggleDarkMode" style="margin-top: 30px;">
        <img src="@/assets/ring.svg" alt="Notifications" class="icon-img" style="margin-top: 30px;">
        <img src="@/assets/uk.svg" alt="English" class="flag" style="margin-top: 30px; width: 20px; height: 20px;">
        
        <!-- قائمة البروفايل -->
        <div class="profile-dropdown" style="margin-top: 20px; margin-right:40px">
          <img src="@/assets/pic2.svg" alt="User" class="profile-pic">
          <div class="btn-group">
            <button type="button" class="dropdown-toggle arrow-only" data-bs-toggle="dropdown"></button>
            <ul class="dropdown-menu">
              <li class="dropdown-header">
                <img src="@/assets/pic2.svg" alt="User" class="dropdown-profile-pic">
                <p class="dropdown-name">John Doe</p>
                <p class="dropdown-email">john@example.com</p>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      isMobileMenuOpen: false,
    };
  },
  mounted() {
    // التحقق من حالة الوضع الداكن المخزنة في localStorage
    if (localStorage.getItem("darkMode") === "enabled") {
      document.documentElement.classList.add("dark-mode");
      document.body.classList.add("dark-mode"); // تطبيقه على `body`
    }
  },
  methods: {
    toggleDarkMode() {
      document.documentElement.classList.toggle("dark-mode");
      document.body.classList.toggle("dark-mode"); // تطبيقه على `body`
      
      // تخزين الحالة في localStorage
      localStorage.setItem(
        "darkMode",
        document.documentElement.classList.contains("dark-mode") ? "enabled" : "disabled"
      );
    },
    toggleMobileMenu() {
      this.isMobileMenuOpen = !this.isMobileMenuOpen;
    }
  }
};
</script>

<style>
/* الوضع الداكن - يطبق الآن على الصفحة بالكامل */
.dark-mode {
  background: #121212 !important;
  color: #ffffff !important;
}

/* تعديل لون الخلفية لكامل الصفحة */
.dark-mode body {
  background: #121212 !important;
}

/* تحسين التباين للنصوص */
.dark-mode p,
.dark-mode span,
.dark-mode a {
  color: #ffffff !important;
}

/* تحسين تنسيق القائمة المنسدلة */
.dark-mode .dropdown-menu {
  background: #1e1e1e !important;
  border-color: #444 !important;
}

/* تحسين تنسيق الأزرار */
.dark-mode .btn {
  background: #333 !important;
  color: #ffffff !important;
}

/* تحسين تنسيق الأيقونات */
.dark-mode .icon-img {
  filter: invert(1);
}

/* تنسيق شريط التنقل في الوضع الداكن */
.dark-mode .navbar {
  background: #1e1e1e !important;
  border-bottom: 1px solid #444;
}

/* شريط التنقل */
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 15px;
  position: relative;
}

.bottom-buttons {
  display: flex;
  gap: 0px;
}

.icon-img {
  width: 20px;
  height: 20px;
}

.top-bar {
  display: flex;
  align-items: center;
  gap: 20px;
}

.profile-pic {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  margin-right: 15px;
  margin-top: 5px;
}

/* زر القائمة عند تصغير الشاشة */
.navbar-toggler {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  position: absolute;
  right: 18px;  
  top: 15px;
  z-index: 1050; 
}

.dropdown-menu {
  left: 0; 
  right: auto;
  min-width: 390px;  
  max-width: 400px;
  border-radius: 8px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
}

.dropdown-header {
  text-align: center; 
  padding: 15px;
}

.dropdown-profile-pic {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  display: block;
  margin: 0 auto 10px; 
}

.dropdown-name,
.dropdown-email {
  margin: 5px 0; 
}

/* تحسين التناسق في الشاشات الصغيرة */
@media (max-width: 768px) {
  .navbar-toggler {
    display: block;
  }

  .top-bar {
    display: none;
    flex-direction: column;
    align-items: center;
    position: relative;
    background: white;
    width: 100%;
    top: 60px;
    left: 0;
    padding: 10px;
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
  }

  .top-bar.show-mobile {
    display: flex;
  }

  .profile-dropdown {
    display: flex;
    align-items: center;
    gap: 4px;
    cursor: pointer;
    justify-content: flex-start;
  }
}

.profile-pic {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  object-fit: cover;
}

.arrow-only {
  background: none;
  border: none;
  padding: 0;
  outline: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}

.arrow-only::after {
  font-size: 16px;
  color: #333;
  transition: transform 0.3s ease;
}

/* عند فتح القائمة، تدوير السهم */
.arrow-only[aria-expanded="true"]::after {
  transform: rotate(180deg);
}

.dropdown-menu {
  right: 100%;
  left: auto;
  transform: translateX(-100px);
  min-width: 280px;
  max-width: 300px;
  border-radius: 8px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
}

.dropdown-item:hover {
  background-color: #f0f0f0;
}
</style>
