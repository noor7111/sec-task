<template>
    <div class="container">
      <!-- Media Section -->
      <h2 class="section-title">
        Media <span class="count">({{ media.length }})</span>
      </h2>
      <div class="media-grid">
        <div v-for="(item, index) in media" :key="index" class="media-item">
          <img :src="item.url" :alt="item.alt" class="media-image" />
        </div>
      </div>
  
      <!-- Files Section -->
      <h2 class="section-title" style="margin-top: 20px;">
        Files <span class="count">({{ files.length }})</span>
      </h2>
      <div class="files-list">
        <div v-for="file in files" :key="file.name" class="file-item">
          <div class="file-icon">
            <img :src="file.url" :alt="file.name" class="file-image" />
          </div>
          <div class="file-info">
            <div class="file-name">{{ file.name }}</div>
            <div class="file-details">
              {{ file.size }} · {{ file.date }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'MediaFilesGallery',
    data() {
      return {
        media: [
          { url: require('@/assets/s1.svg'), alt: 'Media 1' },
          { url: require('@/assets/s2.svg'), alt: 'Media 2' },
          { url: require('@/assets/s3.svg'), alt: 'Media 3' },
          { url: require('@/assets/s4.svg'), alt: 'Media 4' },
          { url: require('@/assets/s1.svg'), alt: 'Media 5' },
          { url: require('@/assets/s2.svg'), alt: 'Media 6' },
        ],
        files: [
          {
            name: 'service-task.pdf',
            size: '2 MB',
            date: '2 Dec 2022',
            url: require('@/assets/m1.svg')
          },
          {
            name: 'homepage-design.fig',
            size: '2 MB',
            date: '2 Dec 2022',
            url: require('@/assets/m2.svg')
          },
          {
            name: 'about-us.html',
            size: '2 MB',
            date: '2 Dec 2022',
            url: require('@/assets/m3.svg')
          },
          {
            name: 'work-project.zip',
            size: '2 MB',
            date: '2 Dec 2022',
            url: require('@/assets/m4.svg')
          },
          {
            name: 'custom.js',
            size: '2 MB',
            date: '2 Dec 2022',
            url: require('@/assets/m5.svg')
          }
        ]
      }
    }
  }
  </script>
<style scoped>
.container {
  padding-left: 15px;
  width: 100%;
  margin-top: 0px; /* رفع المحتوى للأعلى */
}


.section-title {
  font-size: 16px;
  font-weight: 400;
  margin-bottom: 15px;
  color: #333;
  margin-top: 15px;
  padding-left: 10px;
}

.count {
  color: #666;
  font-weight: normal;
}

.media-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2px;
  padding-left: 10px;
}

.media-item {
  border-radius: 16px;
  overflow: hidden;
}

.media-image {
  width: 60px;
  height: 60px;
  object-fit: cover;
  border-radius: 14px;
}

.files-list {
  display: flex;
  flex-direction: column;
  gap: 15px;
  padding-left: 10px;

}

.file-item {
  display: flex;
  align-items: center;
  gap: 12px;
}

.file-icon {
  width: 40px;
  height: 40px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 12px;
  font-weight: 600;
}

.file-info {
  flex: 1;
  
}

.file-name {
  font-size: 12px;
  color: #333;
  margin-bottom: 5px;
}

.file-details {
  font-size: 10px;
  color: #666;
}



/* Responsive Design for smaller screens */
@media (max-width: 768px) {
  .media-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr); /* 3 صور لكل صف */
    gap: 3px; /* مسافة بين الصور */
    justify-content: center; /* محاذاة العناصر في المنتصف */
    align-items: center;
  }

  .media-image {
    width: 70px;
    height: 70px;
    object-fit: cover; /* لضمان تناسب الصور */
  }
}

@media (max-width: 480px) {
  .media-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr); /* 3 صور في كل صف حتى في الشاشات الصغيرة */
    gap: 8px;
    justify-content: center;
    align-items: center;
  }

  .media-image {
    width: 60px;
    height: 60px;
    object-fit: cover;
  }
}


</style>
  