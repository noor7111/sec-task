<template>
    <div class="container-fluid">
        <div class="row">
            <!-- Navbar -->
            <div class="col-12">
                <NavBar />
            </div>
        </div>
    
        <div class="row">
            <div class="col-md-2 sidebar-container">
                <SideBar />
            </div>
    
            <div class="col-md-9 content-container px-5">
                <div class="row">
                    <div class="col-12 header-section">
                        <HeaderSec />
                    </div>
    
                    <div class="d-flex content-layout">
                        <div class="col-4 media-sec" style="border-right: 1px solid #ddd;">
                            <MediaSec />
                        </div>
                        <div class="col-8 chat-container">
                            <div class="row">
                                <div class="col-12 chat-away">
                                    <ChatAway />
                                </div>
                                <div class="shared-background d-flex chat-sections">
                                    <div class="col-8 chat-section" style="border-right: 1px solid #ddd; background-color: white;">
                                        <div class="section">
                                            <ChatSection />
                                        </div>
                                    </div>
                                    <div class="col-4 extra-sec" style="background-color: white; border-bottom-right-radius: 10px;">
                                        <div class="section extra-section">
                                            <ExtraSec />
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import SideBar from './components/SideBar.vue'
import NavBar from './components/NavBar.vue'
import HeaderSec from './components/HeaderSec.vue'
import MediaSec from './components/MediaSec.vue'
import ChatAway from './components/ChatAway.vue'
import ChatSection from './components/ChatSection.vue'
import ExtraSec from './components/ExtraSec.vue'

export default {
    name: 'App',
    components: {
        NavBar,
        SideBar,
        HeaderSec,
        MediaSec,
        ChatAway,
        ChatSection,
        ExtraSec
    }
}
</script>

<style>
/* أساسيات */
.content-container {
    background-color: #F4F7FB;
    max-width: 65%;
    margin-left: auto;
    margin-right: 50px;
    padding: 20px 70px;
    border-radius: 10px;
    transition: all 0.3s ease;
}

/* تخصيص الأقسام */
.sidebar-container {
    transition: all 0.3s ease;
}

/* تعديلات الوسائط */
@media (max-width: 768px) {
    .content-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 20px 10px;
        justify-content: center;
        max-width: 100%;
    }

    .content-layout {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 100%;
    }

    .header-section {
        width: 96% !important;
        max-width: 1400px !important;
        margin: 0 auto 20px 40px;
        padding: 1px 500px;
        background-color: white;
        border-radius: 10px;
        box-sizing: border-box;
    }

    .media-sec {
        width: 80% !important;
        max-width: 1200px !important;
        margin: 0 auto 15px 30px;
        border-radius: 10px !important;
        background-color: white;
        border: none !important;
        box-shadow: none !important;
        padding: 15px;
        overflow: visible !important;
    }

    .chat-away {
        width: 96% !important;
        max-width: 1200px !important;
        margin: 0 auto 15px 40px;
        border: none !important;
        border-radius: 10px !important;
        background-color: white;
        box-shadow: none !important;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
        padding: 20px;
    }

    .chat-section {
        width: 80% !important;
        max-width: 1200px !important;
        margin: 0 auto 15px 30px;
        border-radius: 10px !important;
        background-color: white;
        border: none !important;
        box-shadow: none !important;
        display: flex;
        flex-direction: column-reverse;
        padding: 20px;
    }

    .extra-sec {
        width: 80% !important;
        max-width: 1200px !important;
        margin: 0 auto 15px 30px;
        border-radius: 10px !important;
        background-color: white;
        border: none !important;
        box-shadow: none !important;
        display: flex;
        flex-direction: column-reverse;
        padding: 20px;
    }

    .section {
        width: 100% !important;
        border-radius: 15px;
        background-color: white;
    }

    .shared-background {
        flex-direction: column;
        width: 100%;
    }

    .col-4,
    .col-8 {
        width: 100% !important;
    }
}
</style>
