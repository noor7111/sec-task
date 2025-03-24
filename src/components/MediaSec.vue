<template>
<div class="media-section">
    <div class="profile-header">
        <div class="avatar-container">
            <img src="@/assets/pic1.svg" class="profile-pic" alt="User" />
            <span class="status-dott"></span>
        </div>
        <div class="profile-info">
            <h5>Mathew Anderson</h5>
            <span>Marketing Director</span>
        </div>
        <button class="menu-btn">&#x22EE;</button>
    </div>

    <div class="search-bar">
        <i class="search-icon bi bi-search"></i>
        <input type="text" placeholder="Search contacts" />
    </div>

    <div class="recent-chats">
        <h6>Recent Chats &#9662;</h6>
        <ul>
            <li v-for="chat in chats" :key="chat.id" class="chat-item">
                <div class="avatar-container">
                    <img :src="chat.avatar" class="chat-avatar" alt="User" />
                    <span class="status-dot" :class="chat.status"></span>
                </div>
                <div class="chat-info">
                    <h5>{{ chat.name }}</h5>
                    <p>{{ chat.lastMessage }}</p>
                </div>
                <span class="chat-time">{{ chat.time }}</span>
            </li>
        </ul>
    </div>
</div>
</template>

<script>
export default {
    data() {
        return {
            chats: [{
                    id: 1,
                    name: "Michell Flintoff",
                    lastMessage: "You: Yesterday was great...",
                    time: "15 minutes",
                    avatar: require('@/assets/pic3.svg'),
                    status: "online"
                },
                {
                    id: 2,
                    name: "Bianca Anderson",
                    lastMessage: "Nice looking dress you...",
                    time: "30 minutes",
                    avatar: require("@/assets/pic4.svg"),
                    status: "busy"
                },
                {
                    id: 3,
                    name: "Andrew Johnson",
                    lastMessage: "Sent a photo",
                    time: "2 hours",
                    avatar: require("@/assets/pic5.svg"),
                    status: "away"
                },
                {
                    id: 4,
                    name: "Mark Strokes",
                    lastMessage: "Lorem ipsum text sud...",
                    time: "5 days",
                    avatar: require("@/assets/pic6.svg"),
                    status: "online"
                },
                {
                    id: 5,
                    name: "Mark, Stoinus & Rish...",
                    lastMessage: "Lorem ipsum text ...",
                    time: "5 days",
                    avatar: require("@/assets/pic7.svg"),
                    status: "offline"
                },
                {
                    id: 6,
                    name: "Bianca Anderson",
                    lastMessage: "Nice looking dress you...",
                    time: "30 minutes",
                    avatar: require("@/assets/pic4.svg"),
                    status: "busy"
                }
            ]
        };
    }
};
</script>

<style scoped>
.content-container {
    width: 100% !important;
    max-width: 100% !important;
    margin: 0 !important;
    padding: 0 !important;

}

.media-section {
    background: #ffffff;
    padding: 20px;
    border-top-left-radius: 10px;
    border-bottom-left-radius: 10px;

}

.profile-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.profile-pic {
    width: 45px;
    height: 45px;
    border-radius: 50%;
}

.profile-info {
    flex-grow: 1;
    margin-left: 10px;

}

.profile-info h5 {
    margin: 0;
    font-size: 16px;

}

.profile-info span {
    font-size: 12px;
    color: #98A4AE;
    font-family: "Arial", sans-serif;
}

.menu-btn {
    background: none;
    border: none;
    font-size: 25px;
    cursor: pointer;
    font-weight: 300; /* سماكة الخط */
    color: #37414A; /* لون النص */
    font-family: "Arial", sans-serif;
}

.search-bar {
    position: relative;
    display: flex;
    align-items: center;
    width: 100%;
    margin-top: 15px;
    border: 1px solid #ddd;
    border-radius: 5px;
    padding: 10px;
    background-color: #fff;
    margin-top: 30px;
    margin-bottom: 48px;
}

.search-bar .search-icon {
    font-size: 16px;
    color: #888;
    margin-right: 10px;
}

.search-bar input {
    flex-grow: 1;
    border: none;
    outline: none;
    font-size: 14px;
}

.recent-chats h6 {
    margin-top: 30px;
    font-size: 14px;
    color: #98A4AE;
    margin-bottom: 15px;
    margin-left: 13px;
}

.recent-chats ul {
    list-style: none;
    padding: 0;
    margin: 0;
    padding-bottom: 0px;
    /* زيادة المسافة تحت */

}

.recent-chats li {
    display: flex;
    align-items: center;
    padding: 10px;
    transition: background-color 0.2s ease;
    box-sizing: border-box;
    width: 100%;
    /* يجعل العنصر يمتد على عرض الحاوية بالكامل */
}

/* تغيير لون الخلفية عند تمرير الماوس بدون تغيير الحجم */
.recent-chats li:hover {
    background-color: #F6F7F9;
    /* لون رمادي فاتح */
    border-radius: 5px;
}

/* تعيين أول محادثة كـ Active */
.recent-chats li:first-child {
    background-color: #F6F7F9;
    /* لون مختلف للمحادثة النشطة */
    border-radius: 5px;

}

.avatar-container {
    position: relative;
    display: inline-block;
}

.chat-avatar {
    width: 40px;
    height: 40px;
    border-radius: 50%;
}

.status-dot {
    width: 1px;
    height: 1px;
    border-radius: 50%;
    position: absolute;
    bottom: 0;
    right: 0;
    border: 1px solid white;
}

.status-dot.online {
    background-color:#36C76C;
    border: 1px solid #36C76C;
    width: 7px;
    height: 7px;
}

.status-dot.offline {
    background-color:#36C76C;
    border: 1px solid #36C76C;
    width: 7px;
    height: 7px;

}

.status-dot.away {
    background-color: #FFD648;
    border: 1px solid #FFD648;
    width: 7px;
    height: 7px;
}

.status-dot.busy {
    background-color: #FF6692;
    border: 1px solid #FF6692;
    width: 7px;
    height: 7px;
}

.status-dot {
    position: absolute;
    bottom: 2px;
    right: 2px;
    width: 10px;
    height: 10px;
    background-color: green;
    border-radius: 50%;
    border: 2px solid white;
}

.status-dott {
    position: absolute;
    bottom: 1px;
    right: 18px;
    width: 7px;
    margin-bottom: 1px;
    margin-left: 5px;
    height: 7px;
    background-color: #36C76C;
    border-radius: 50%;
    border: 1px solid #36C76C;
}

.chat-info {
    flex-grow: 1;
    margin-left: 10px;
}

.chat-info h5 {
    margin: 0;
    font-size: 14px;
    
    color: #37414A; /* لون النص */
    font-family: 'Raleway', sans-serif;
}

.chat-info p {
    margin: 0;
    font-size: 12px;
    color: #888;
    margin-bottom: 4px;
}

.chat-time {
    font-size: 11px;
    color: #98A4AE;
    margin-bottom: 20px;
    font-family: "Oktah Neue", sans-serif;
    font-weight: 20;
    /* سمك الخط */
    letter-spacing: 0.2px;
    /* تباعد بين الحروف */
    line-height: 1.2;
    /* ارتفاع السطر */
}

/* Media Queries for responsiveness */
@media (max-width: 768px) {
    .content-container {
        width: 40% !important;
        height: auto !important;
        max-height: none !important;
    }

    .row {
        margin-left: 0 !important;
        margin-right: 0 !important;
        width: 100% !important;
    }

    .sidebar-container {
        display: none;
    }

    .content-layout,
    .media-chat-container,
    .shared-background {
        width: 100% !important;
        max-width: 100% !important;
        margin: 0 !important;
        padding: 0 !important;
    }

    .header-section,
    .media-sec,
    .chat-away,
    .chat-section-wrapper,
    .extra-sec-wrapper {
        width: 100% !important;
        max-width: 100% !important;
        margin: 5px 0 !important;
        border-radius: 0;
    }
}

@media (max-width: 480px) {
    .container-fluid {
        padding: 0 !important;
    }

    .content-container {
        max-width: 100% !important;
        padding: 2px !important;
        border-radius: 0 !important;
    }
}
</style>
