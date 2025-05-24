<script setup>
import { ref, onMounted } from 'vue';

const NUM_INTERP_FRAMES = 6;
const categories = ['cat', 'dog', 'ship', 'airplane'];
const categoryChineseNames = {
  'cat': '猫',
  'dog': '狗',
  'ship': '船',
  'airplane': '飞机'
};
const imagePaths = {
  dog: [],
  cat: [],
  ship: [],
  airplane: []
};
const imageRootPath = './q_image/';
const minValue = 0;
const maxValue = 5;
const sliderLabels = ['clean', '4/255', '8/255', '10/255', '12/255', '16/255'];

let currentImages = ref({
  dog: "",
  cat: "",
  ship: "",
  airplane: ""
});
let sliderValue = ref(0);
let isLoading = ref(true);

const preloadImages = () => {
  const promises = [];

  categories.forEach(category => {
    for (let i = 0; i < NUM_INTERP_FRAMES; i++) {
      const path = `${imageRootPath}${category}_${i+1}.png`;
      const img = new Image();
      imagePaths[category][i] = img;
      const promise = new Promise((resolve) => {
        img.onload = resolve;
      });
      img.src = path;
      promises.push(promise);
    }
  });

  return Promise.all(promises).then(() => {
    isLoading.value = false;
    console.log("preloadImages finished");
  });
}

onMounted(() => {
    preloadImages();
    handleChange(0);
});

const handleChange = (value) => {
  const newImages = {};
  categories.forEach(category => {
    newImages[category] = imagePaths[category][value].src;
  });
  currentImages.value = newImages;
};

</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
      <h1 class="section-title">Qualitative Results</h1>
    </el-row>

    <el-row justify="center">
      <el-col>
        <el-row justify="center" :gutter="20">
          <el-col v-for="category in categories" :key="category" 
                  :xs="12" :sm="6" :md="6" :lg="3" :xl="3">
            <div class="demo-image">
              <div class="block">
                <el-skeleton
                  style="width: 100%"
                  :loading="isLoading"
                  animated
                  :throttle="1000">
                  <template #template>
                    <el-skeleton-item variant="image" style="width: 100%; height: 100%" />
                  </template>
                  <template #default>
                    <img :src="currentImages[category]" style="width: 100%; object-fit: contain;">
                  </template>
                </el-skeleton>
                <span class="demonstration">{{ categoryChineseNames[category] }}</span>
              </div>
            </div>
          </el-col>
        </el-row>
      </el-col>
    </el-row>

    <!-- 滑块控制 -->
    <el-row justify="center">
      <el-col :span="12">
          <el-slider 
            v-model="sliderValue" 
            :min="minValue" 
            :max="maxValue" 
            :marks="sliderLabels.reduce((acc, label, index) => {
              acc[index] = { label, style: { color: '#666' } };
              return acc;
            }, {})"
            :show-tooltip="false"
            @input="handleChange"/>
      </el-col>
    </el-row>

  </div>
</template>

<style scoped>
/* 滑块 */
.el-slider {
  margin: 15px 0;
}

/* 路径文字居中 */
.demo-image .block {
  padding: 20px 0 0 0;
  text-align: center;
  border-right: solid 1px var(--el-border-color);
  display: inline-block;
  width: 100%;
  box-sizing: border-box;
  vertical-align: top;
}

.demo-image .block:last-child {
  border-right: none;
}

/* 路径文字颜色 */
.demo-image .demonstration {
  padding-top: 10px;
  display: block;
  color: var(--el-text-color-secondary);
  word-wrap: break-word;
}

/* 滑块背景颜色 */
.el-slider__runway {
  background-color: #c6c6c6;
}

.section-title {
  margin-bottom: 20px;
  color: #333;
}
</style>