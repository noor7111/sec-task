<template>
    <div class="chat-container">
        <div class="chat-box">
            <div class="message-container" :class="{'sent-message-container': msg.type === 'sent'}" v-for="(msg, index) in messages" :key="index">
                <img v-if="msg.type === 'received' || msg.type === 'receivedd'" src="@/assets/pic5.svg" class="profile-pic" alt="Profile" />
    
                <div class="message-content">
                    <div class="message-header" v-if="msg.sender || msg.time">
                        <span class="message-time" :class="{'sent-time': msg.type === 'sent'}">{{ msg.sender ? msg.sender + ', ' : '' }}{{ msg.time }}</span>
                    </div>
    
                    <div class="message" :class="msg.type">
                        <span v-if="msg.text">{{ msg.text }}</span>
                        <img v-if="msg.imgSrc" :src="msg.imgSrc" alt="Sent Image" class="message-image" />
                    </div>
                </div>
            </div>
        </div>
    
        <div class="message-input-container">
            <button class="icon-button">
                <img src="@/assets/smile.svg" alt="Emoji" />
            </button>
            <input type="text" class="message-input" placeholder="Type a Message" />
            <button class="icon-button" @click="togglePopup('image')">
                <img src="@/assets/add.svg" alt="Image" />
            </button>
            <button class="icon-button" @click="togglePopup('file')">
                <img src="@/assets/add2.svg" alt="Attach" />
            </button>
            <button class="icon-button" @click="togglePopup('voice')">
                <img src="@/assets/add3.svg" alt="Mic" />
            </button>
        </div>
    
        <div v-if="activePopup === 'image'" class="popup-overlay" @click="togglePopup(null)">
            <div class="popup-content" @click.stop>
                <img src="@/assets/in1.svg" alt="Image" />
                <h5>unlock user</h5>
                <p>You are about to upload an image. Are you sure?</p>
                <button class="popup-button" @click="togglePopup(null)">Cancel</button>
                <button class="popupp-button" @click="confirmAction">Yes</button>
            </div>
        </div>
    
        <div v-if="activePopup === 'file'" class="popup-overlay" @click="togglePopup(null)">
            <div class="popup-content" @click.stop>
                <img src="@/assets/in2.svg" alt="File" />
                <h5>Delete Conversation</h5>
                <p>once you sure to delete this conversation, you<br> will not be able to undo this action</p>
                <button class="popup-button" @click="togglePopup(null)">Cancel</button>
                <button class="popupp-button" @click="confirmAction">Yes</button>
            </div>
        </div>
    
        <div v-if="activePopup === 'voice'" class="popup-overlay" @click="togglePopup(null)">
            <div class="popup-content" @click.stop>
                <img src="@/assets/in3.svg" alt="Mic" />
                <h5>Block User</h5>
                <p>you are going to block this user , are you
                    sure?</p>
                <button class="popup-button" @click="togglePopup(null)">Cancel</button>
                <button class="popupp-button" @click="confirmAction">Yes</button>
            </div>
        </div>
    </div>
    </template>
    
    <script>
    export default {
        data() {
            return {
                messages: [{
                        sender: 'Andrew',
                        time: '2 hours ago',
                        text: "If I don't like something, I'll stay away from it.",
                        type: 'received'
                    },
                    {
                        text: "If I don't like something, I'll stay away from it.",
                        time: '2 hours ago',
                        type: 'sent'
                    },
                    {
                        sender: 'Andrew',
                        time: '2 hours ago',
                        text: "I want more detailed information.",
                        type: 'received'
                    },
                    {
                        text: "If I don’t like something, I’ll stay away from it.",
                        time: '2 hours ago',
                        type: 'sent'
                    },
                    {
                        text: "They got there early, and they got really good seats.",
                        type: 'sent'
                    },
                    {
                        sender: 'Andrew',
                        time: '2 hours ago',
                        imgSrc: require('@/assets/pink.svg'),
                        type: 'receivedd'
                    }
    
                ],
                activePopup: null,
            };
        },
        methods: {
            togglePopup(type) {
                this.activePopup = type;
            },
            confirmAction() {
                console.log("✅ Action confirmed");
                this.togglePopup(null);
            }
        }
    };
    </script>
    
    <style scoped>
.chat-container {
    display: flex;
    flex-direction: column;
    height: 65vh;
}

.chat-box {
    flex-grow: 1;
    overflow-y: auto;
    padding: 0px;
    scrollbar-width: none;
    -ms-overflow-style: none;
}

.chat-box::-webkit-scrollbar {
    display: none;
}

.popup-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 999;
}

.popup-content {
    background: white;
    padding: 20px;
    border-radius: 10px;
    text-align: center;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
}

.popup-button {
    margin: 0 10px;
    padding: 10px 20px;
    border: none;
    background: #959595;
    color: white;
    border-radius: 5px;
    cursor: pointer;
    width: 100px;
    height: 40px;
}

.popupp-button {
    margin: 0 10px;
    padding: 10px 20px;
    border: none;
    background: #575CD4;
    color: white;
    border-radius: 5px;
    cursor: pointer;
    width: 100px;
    height: 40px;
}

.message-time {
    font-size: 12px;
    color: #777;
}

.message-container {
    display: flex;
    align-items: flex-start;
    gap: 5px;
    margin-bottom: 5px;
    width: 100%;
    justify-content: flex-start;
}

.message-container.sent-message-container {
    justify-content: flex-end;
}

.message-content {
    max-width: 100%;
}

.sent {
    background: #ECFDFD;
    padding: 10px 15px;
    border-radius: 10px;
    font-size: 11.5px;
    text-align: right;
    margin-left: 0;
    max-width: 100%;
    border-top-right-radius: 0px;
    border-bottom-right-radius: 0px;


}

.message-time {
    font-size: 12px;
    color: #777;
    margin-bottom: 5px;


}

.profile-pic{
    margin-left: 20px;


}

.sent-time {
    display: block;
    text-align: right;
    margin-left: 50px;
}


.received {
    background: #EFF4FA;
    padding: 10px 15px;
    border-radius: 5px;
    font-size: 11.5px;

}

.receivedd {
    padding: 10px 1px;
    
}

.message-input-container {
    display: flex;
    align-items: center;
    padding: 5px;
    background: white;
    border-top: 1px solid #ddd;
    position: sticky;
    bottom: 0;
    width: 100%;
}

.icon-button {
    background: none;
    border: none;
    cursor: pointer;
}

.icon-button img {
    width: 20px;
    height: 20px;
}

.message-input {
    flex-grow: 1;
    border: none;
    outline: none;
    font-size: 16px;
    padding: 5px 10px;
}

/* Media Queries for responsiveness */

@media (max-width: 1024px) {
    .chat-container {
        height: auto;
    }
  
    .message-input-container {
        padding: 10px;
        font-size: 14px;
    }

    .message-input {
        font-size: 14px;
    }

    .message-container {
        gap: 5px;
    }

    .popup-content {
        width: 90%;
        padding: 15px;
    }
}

@media (max-width: 768px) {
    .message-container {
        flex-direction: column;
        gap: 10px;
    }

    .sent {
        font-size: 14px;
        max-width: 90%;
        margin-left: 290px;
        
    }

    .received {
        font-size: 14px;
        max-width: 90%;
    }

    .message-input-container {
        padding: 15px;
    }

    .icon-button img {
        width: 18px;
        height: 18px;
    }

    .message-input {
        font-size: 14px;
    }
}

@media (max-width: 480px) {
    .chat-container {
        height: auto;
    }

    .message-input-container {
        padding: 10px;
    }

    .message-input {
        font-size: 12px;
    }

    .icon-button img {
        width: 16px;
        height: 16px;
    }

    .sent {
        font-size: 12px;
    }

    .received {
        font-size: 12px;
    }

    .popup-content {
        padding: 10px;
    }

    .popup-button, .popupp-button {
        width: 80px;
        height: 35px;
    }
}
</style>
