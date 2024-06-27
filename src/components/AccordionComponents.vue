<script setup>
import { reactive } from 'vue'

const data = reactive([
  {
    icon: '/icon_engine.png',
    name: 'engine',
    title: 'Мощность двигателя',
    options: [
      { value: 300, prefix: 'л.с.' },
      { value: 400, prefix: 'л.с.' },
      { value: 500, prefix: 'л.с.' }
    ],
    isOpen: false
  }, {
    icon: '/icon_volume.png',
    name: 'volume',
    title: 'Объем кузова',
    options: [{ value: 300, prefix: 'л.с.' }],
    isOpen: false
  }, {
    icon: '/icon_bad.png',
    name: 'bad',
    title: 'Спальные места',
    options: [{ value: 300, prefix: 'л.с.' }],
    isOpen: false
  }, {
    icon: '/icon_fuel.png',
    name: 'fuel',
    title: 'Топливный бак',
    options: [{ value: 300, prefix: 'л.с.' }],
    isOpen: false
  }, {
    icon: '/icon_transmission.png',
    name: 'transmission',
    title: 'Коробка передач',
    options: [{ value: 300, prefix: 'л.с.' }],
    isOpen: false
  }
])

const openAccardion = (option) =>
  option.isOpen = !option.isOpen


</script>

<template>
  <div class="accordion">
    <div class="accordion_container">
      <div
        @click="openAccardion(option)"
        :key="option.icon"
        v-for="(option) of data"
        class="accordion-item"
        :class="option.isOpen ? 'active' : ''"
      >
        <div class="accordion-head">
          <div class="accordion-head_info">
            <img
              class="accordion-head_image"
              :src="`image/${option.icon}`"
              :alt="option.name"
              :draggable="false"
            />
            <h2 class="accordion-head_title">{{ option.title }}</h2>
          </div>
          <button
            @click.stop="openAccardion(option)"
            class="accordion-head_button"
            :class="option.isOpen ? 'close' : 'open'"
          />
        </div>
        <div :class="option.isOpen ? 'active' : ''" class="accordion-content">
          <div @click.stop class="accordion-radio" :key="buttons.value" v-for="(buttons, idx) of option.options">
            <input
              :id="option.name+buttons.value"
              type="radio"
              :name="option.name"
              :checked="idx === 0"
            >
            <label :for="option.name+buttons.value">{{ buttons.value }}{{ buttons.prefix }}</label>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<style scoped>
.accordion {
  position: relative;
  max-width: 429px;
  height: 316px;
}

.accordion_container {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
}

.accordion-item {
  position: relative;
  border-top: 1px solid #000;
  border-bottom: 1px solid #000;
  transition: padding-bottom .4s ease-in;
  padding-bottom: 0;
}

.accordion-item.active {
  padding-bottom: 50px;
}

.accordion-item:first-of-type {
  border-top: 2px solid #000;
}

.accordion-item:last-of-type {
  border-bottom: 2px solid #000;
}

.accordion-head {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.accordion-head_info {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 14px;
}

.accordion-head_image {
  object-fit: cover;
}

.accordion-head_title {
  //font-family: ;
  font-size: 1rem;
  font-weight: 800;
}

.accordion-head_button {
  width: 25px;
  height: 25px;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
  background-color: transparent;
  border: none;
  cursor: pointer;
}

.close {
  background-image: url("/image/icon_minus.png");
}

.open {
  background-image: url("/image/icon_plus.png");
}

.accordion-item:nth-child(2) .accordion-head_info {
  position: relative;
  gap: 5px;
}

.accordion-item:nth-child(2) .accordion-head_image {
  position: absolute;
  left: -15px;
}

.accordion-item:nth-child(2) .accordion-head_title {
  padding-left: 39px;
}

.accordion-content {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 30px;
  //font-family: ;
  font-size: 13px;
  font-weight: 800;
  position: absolute;
  opacity: 0;
  visibility: hidden;
  top: 0;
  padding: 0 37px;
  transition: all .4s ease-in;
  accent-color: green;
}

.accordion-radio {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 5px;
}

.accordion-radio input {
  margin: 0;
  background-color: gray;
}

.accordion-content.active {
  visibility: visible;
  opacity: 1;
  transform: translateY(40px);
}


</style>