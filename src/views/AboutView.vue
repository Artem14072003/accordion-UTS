<template>
  <div class="about">
    <h1 class="text-dark">Это Аккардион, был сделан, для моего друга! &#128513;</h1>
  </div>
</template>

<style scoped>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}

.text-dark {
  font-size: clamp(24px, 5vw, 48px);
}
</style>
