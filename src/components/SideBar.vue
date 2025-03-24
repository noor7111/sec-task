<template>
    <div>
        <!-- زر فتح القائمة في الشاشات الصغيرة -->
        <button class="menu-toggle" @click="toggleSidebar">
            <i class="bi bi-list"></i>
        </button>
    
        <div :class="['sidebar', { 'sidebar-collapsed': isCollapsed }]">
            <div class="logo-container">
                <img src="@/assets/loogo.svg" alt="Logo" class="logo" />
            </div>
            <ul class="menu-list">
                <li class="menu-item active" style="box-shadow: 0 6px 6px rgba(0, 0, 0, 0.1);"><i class="bi bi-house-door"></i><span v-if="!isCollapsed">Dashboard</span></li>
                <li class="menu-item"><i class="bi bi-box-seam" style="color: #98A4AE;"></i><span v-if="!isCollapsed">Orders</span></li>
                <li class="menu-item"><i class="bi bi-people-fill" style="color: #98A4AE;"></i><span v-if="!isCollapsed">Passengers</span></li>
                <li class="menu-item"><i class="bi bi-bus-front-fill" style="color: #98A4AE;"></i><span v-if="!isCollapsed">Captains</span></li>
                <li class="menu-item"><i class="bi bi-menu-app" style="color: #98A4AE;"></i><span v-if="!isCollapsed">Categories</span></li>
                <hr />
                <li class="menu-item"><i class="bi bi-card-text" style="color: #98A4AE;"></i><span v-if="!isCollapsed">Settlement</span></li>
                <hr />
                <li class="menu-item"><i class="bi bi-wechat" style="color: #98A4AE;"></i><span v-if="!isCollapsed">Contact</span></li>
                <li class="menu-item"><i class="bi bi-star-half" style="color: #98A4AE;"></i><span v-if="!isCollapsed">Reviews</span></li>
                <hr />
                <li class="menu-item dropdown" @mouseenter="showDropdown = true" @mouseleave="showDropdown = false">
                    <a href="#" class="dropdown-toggle" style="color: #29343D;">
                        <i class="bi bi-shield-lock" style="color: #98A4AE;"></i><span v-if="!isCollapsed">Permissions</span>
                    </a>
                    <ul v-show="showDropdown" class="dropdown-menu" style="position: absolute; left: 100%; top: 0; width: 200px; background: white; border-radius: 8px; box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1); z-index: 1000; padding: 10px;">
                        <li><a href="#" style="color: #29343D; display: block; margin-bottom: 8px; font-size: 13px;">You have permission</a></li>
                        <li><a href="#" style="color: #29343D; font-size: 13px;">You do not have permission</a></li>
                    </ul>
                </li>
                <li class="menu-item"><i class="bi bi-microsoft-teams" style="color: #98A4AE;"></i><span v-if="!isCollapsed">Translation</span></li>
                <li class="menu-item"><i class="bi bi-film" style="color: #98A4AE;"></i><span v-if="!isCollapsed">Education Video</span></li>
                <li class="menu-item"><i class="bi bi-gear" style="color: #98A4AE;"></i><span v-if="!isCollapsed">Settings</span></li>
                <li class="menu-item"><i class="bi bi-file-text" style="color: #98A4AE;"></i><span v-if="!isCollapsed">Content</span></li>
            </ul>
        </div>
    </div>
</template>
    
<script>
export default {
    name: "SidebarMenu",
    data() {
        return {
            isCollapsed: window.innerWidth <= 768,
            showDropdown: false,
        };
    },
    methods: {
        toggleSidebar() {
            this.isCollapsed = !this.isCollapsed;
        },
        handleResize() {
            this.isCollapsed = window.innerWidth <= 768;
        },
    },
    mounted() {
        window.addEventListener("resize", this.handleResize);
    },
    beforeUnmount() {
        window.removeEventListener("resize", this.handleResize);
    },
};
</script>
    
<style scoped>
/* الزر الذي يظهر فقط في الشاشات الصغيرة */
.menu-toggle {
    display: none;
    position: absolute;
    top: 10px;
    left: 10px;
    background: #635bff;
    color: white;
    border: none;
    padding: 10px 15px;
    font-size: 18px;
    border-radius: 5px;
    cursor: pointer;
}

/* القائمة الجانبية */
.sidebar {
    width: 250px;
    height: 70px;
    background: white;
    padding: 20px;
    position: fixed;
    top: 0;
    left: 0;
    transition: width 0.3s ease-in-out;
}

.logo-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-left: 70px;
}


/* تصغير القائمة عند الطي */
.sidebar-collapsed {
    width: 60px;
}

/* العناصر داخل القائمة */
.menu-list {
    list-style: none;
    padding: 0;
    margin-top: 20px;
}

.menu-item {
    padding: 9px;
    display: flex;
    align-items: center;
    font-size: 14px;
    color: #29343D;
    cursor: pointer;
    transition: 0.3s;
}

.menu-item i {
    margin-right: 10px;
}

/* عند تحريك الفأرة فوق العناصر */
.menu-item:hover,
.menu-item.active {
    background: #635bff;
    color: white;
    border-radius: 10px;
}

.menu-item:hover i {
    color: white !important;
}

/* إزالة التسطير من الروابط */
.dropdown-toggle {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    /* يجعل السهم يذهب إلى أقصى اليمين */
}

.dropdown-toggle i {
    margin-right: 8px;
}

.dropdown-toggle::after {

    font-size: 20px;
    margin-left: auto;
}

.dropdown-toggle {
    text-decoration: none
}


.dropdown-menu {
    width: 200px;
    max-height: 300px;
    overflow-y: auto;
    padding: 10px;
    background: white;
    border-radius: 8px;
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);

}

.dropdown:hover .dropdown-menu {
    display: block;
}

.dropdown-menu a {
    text-decoration: none;
    display: block;
    padding: 5px 5px;
    transition: background 0.3s, color 0.3s;
}

/* عند تمرير السهم عليها، يتغير اللون */
.dropdown-menu a:hover {
    background: #635bff;
    color: white !important;
    border-radius: 5px;
}

/* عند تمرير الماوس على عنصر Permissions، يتغير لون النص فقط */
.menu-item.dropdown:hover .dropdown-toggle {
    color: white !important;
}

hr {
    margin: 5px 0;
    border: none;
    height: 1px;
    background-color: #98A4AE;
    width: 100%;
}

/* شاشات متوسطة وصغيرة */
@media (max-width: 1024px) {
    .sidebar {
        width: 80px;
        padding: 10px;
    }

    .menu-item span {
        display: none;
    }
}

/* شاشات الجوال */
@media (max-width: 768px) {
    .menu-toggle {
        display: block;
    }

    .sidebar {
        width: 60px;
        padding: 5px;
    }

    .menu-item {
        justify-content: center;
    }

    .menu-item i {
        font-size: 18px;
    }
}


/* القائمة الجانبية */
.sidebar {
    width: 250px;
    height: 100vh; /* ارتفاع الشريط الجانبي ليغطي كامل الشاشة */
    background: white;
    padding: 20px;
    position: fixed; /* لتثبيت الشريط الجانبي في المكان */
    top: 0;
    left: 0;
    transition: width 0.3s ease-in-out;
    z-index: 1000; /* ضمان بقاء الشريط الجانبي فوق العناصر الأخرى */
}

/* تصغير القائمة عند الطي */
.sidebar-collapsed {
    width: 60px;
}

/* عند الشاشات الصغيرة، ستظل القائمة ثابتة في مكانها */
@media (max-width: 768px) {
    .sidebar {
        width: 60px;
        padding: 5px;
    }
}

</style>  