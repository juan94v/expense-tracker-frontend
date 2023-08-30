<template>
  <div class="h-screen flex items-center justify-center">
    <div class="neon-text text-9xl font-bold text-white">
      <span
        class="neon-letter inline-block transform transition-transform duration-1000"
        :class="currentColorClass"
        v-for="(letter, index) in neonText"
        :key="index"
      >
        {{ letter }}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      neonText: 'About Page'.split(''), // Texto que deseas animar
      currentColorIndex: 0, // Índice del color actual (0: rojo, 1: verde, 2: azul)
      colors: ['text-red-500', 'text-green-500', 'text-blue-500'], // Clases de colores de Tailwind CSS
    };
  },
  computed: {
    currentColorClass() {
      return this.colors[this.currentColorIndex];
    },
  },
  methods: {
    changeColor() {
      this.currentColorIndex = (this.currentColorIndex + 1) % this.colors.length;
    },
  },
  mounted() {
    setInterval(this.changeColor, 3000); // Cambio de color cada 3 segundos
  },
};
</script>

<style scoped>
.neon-letter {
  animation: neonAnimation 3s linear infinite;
  margin: 0 10px;
  text-shadow: 0 0 10px rgba(255, 255, 255, 0.8); /* Agregamos un sombreado brillante */
}

@keyframes neonAnimation {
  0% {
    color: red;
  }
  33% {
    color: green;
  }
  66% {
    color: blue;
  }
  100% {
    color: red;
  }
}
</style>
