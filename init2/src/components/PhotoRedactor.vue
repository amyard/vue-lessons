<template>
  <div class="container">
    <div class="flex">
      <div class="img-wrapper">
        <img 
            v-if="isCatVisible" 
            :class="imgFilters"
            :style="imgStyles"
            src="../assets/images/cat.jpg" alt="">
        <p v-else>Cat will be sone here!!!</p>
      </div>
      <div class="controls">
        <h1>Shaverma</h1>
        <h2>Filters</h2>
        
        <button type="button" 
                :class="imgFilters.sepia ? 'active' : ''"
                @click="imgFilters.sepia = !imgFilters.sepia">Сепия</button>
        
        <button type="button"
                :class="imgFilters.border ? 'active' : ''"
                @click="imgFilters.border = !imgFilters.border">Рамка</button>

        <button type="button"
                :class="imgFilters.small ? 'active' : ''"
                @click="imgFilters.small = !imgFilters.small">Уменьшить</button>

        <button type="button"
                :class="imgFilters.shadow ? 'active' : ''"
                @click="imgFilters.shadow = !imgFilters.shadow">Shadow</button>

        <h2>Размер</h2>
        <div class="btn-group">
          <label>
            Ширина: {{ imgSizes.currentWidth }}
            <input
                type="range"
                :value="imgSizes.currentWidth"
                @input="imgSizes.currentWidth = $event.target.value"
                :min="imgSizes.minWidth"
                :max="imgSizes.maxWidth"
            >
          </label>
          <label>
            Высота: {{ imgSizes.currentHeight }}
            <input
                type="range"
                :value="imgSizes.currentHeight"
                @input="imgSizes.currentHeight = $event.target.value"
                :min="imgSizes.minHeight"
                :max="imgSizes.maxHeight"
            >
          </label>
        </div>

        <h2>Rotate</h2>
        <div class="btn-group">
          <label>
            Degree: {{ rotate.currentValue }}
            <input
                type="range"
                :value="rotate.currentValue"
                @input="rotate.currentValue = $event.target.value"
                :min="rotate.minValue"
                :max="rotate.maxValue"
            >
          </label>
        </div>

        <button @click="isCatVisible = !isCatVisible">
          {{isCatVisible ? 'Hide' : 'Show'}}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PhotoRedactor",
  data() {
    return {
      isCatVisible: true,
      imgFilters: {
        sepia: false,
        border: false,
        small: false,
        shadow : false
      },
      imgSizes: {
        maxWidth: 680,
        maxHeight: 480,
        currentWidth: 680,
        currentHeight: 480,
      },
      rotate: {
        minValue: 0,
        maxValue: 360,
        currentValue: 0
      }
    }
  },
  computed: {
    imgStyles() {
      return {
        width: `${this.imgSizes.currentWidth}px`,
        height: `${this.imgSizes.currentHeight}px`,
        transform: `rotate(${this.rotate.currentValue}deg)`
      }
    }
  }
}
</script>

<style scoped>
.container {
  margin-top: 40px;
}
.controls {
  margin-left: 20px;
}
.img-wrapper {
  width: 640px;
  height: 480px;
  background-color: #cecece;
}
img {
  transition: 0.2s ease;
}
img.sepia {
  filter: sepia(100%);
}
img.border {
  border: 5px dashed #464646
}
img.small {
  width: 400px;
}

img.shadow {
  box-shadow: 7px 7px 10px 0 #7e7e7e;
}

button {
  margin-right: 10px;
}
button.active {
  background-color: #dbdbdb;
}
h2 {
  margin-bottom: 10px;
}
.btn-group {
  margin-bottom: 20px;
}
input[type="range"] {
  display: block;
}
</style>
