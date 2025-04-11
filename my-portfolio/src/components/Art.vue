<template>
    <section class="illustrations-section py-16 px-8">
      <h2 class="text-4xl font-bold text-gray-900 mb-10 text-left">Art & Play</h2>
      
      <!-- Images and Text Container -->
      <div class="illustrations-container grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <!-- Image 1 -->
        <div class="illustration-image">
          <img src="/visuals/illustration1.jpg" alt="Illustration 1" class="w-full h-auto object-cover"/>
        </div>
        
        <!-- Image 2 -->
        <div class="illustration-image">
          <img src="/visuals/illustration2.jpg" alt="Illustration 2" class="w-full h-auto object-cover"/>
        </div>
        
        <!-- Image 3 -->
        <div class="illustration-image">
          <img src="/visuals/illustration3.jpg" alt="Illustration 3" class="w-full h-auto object-cover"/>
        </div>
        
        <!-- Image 4 -->
        <div class="illustration-image">
          <img src="/visuals/illustration4.jpg" alt="Illustration 4" class="w-full h-auto object-cover"/>
        </div>
  
        <!-- Image 5 (Horizontal) -->
        <div class="illustration-image col-span-2">
          <img src="/visuals/illustration5.jpg" alt="Illustration 5" class="w-full h-auto object-cover"/>
        </div>
  
        <!-- Image 6 (Vertical) -->
        <div class="illustration-image">
          <img src="/visuals/illustration7.jpg" alt="Illustration 7" class="w-full h-auto object-cover"/>
        </div>

        <!-- Image 7 (Horizontal) -->
        <div class="illustration-image col-span-2">
          <img src="/visuals/illustration6.jpg" alt="Illustration 6" class="w-full h-auto object-cover"/>
        </div>

        <!-- Image 8 (Vertical) -->
        <div class="illustration-image">
          <img src="/visuals/knock.jpg" alt="Illustration 8" class="w-full h-auto object-cover"/>
        </div>

        <!-- Image 9 (Horizontal) -->
        <div class="illustration-image col-span-2">
          <img src="/visuals/painting1.jpeg" alt="Illustration 9" class="w-full h-auto object-cover"/>
        </div>

        <!-- Image 10 (Vertical) -->
        <div class="illustration-image">
          <img src="/visuals/painting2.jpg" alt="Illustration 8" class="w-full h-auto object-cover"/>
        </div>

        <!-- Image 11 (Horizontal) -->
        <div class="illustration-image col-span-2">
          <img src="/visuals/art.jpg" alt="Illustration 11" class="w-full h-auto object-cover"/>
        </div>
      </div>
  
      <!-- Text below images -->
      <div class="text-container mt-8 text-center">
        <h3 class="text-2xl font-semibold text-gray-800">My name is Daria, and I’m here to break free from challenges!</h3>
        <p class="mt-4 text-lg text-gray-600 max-w-3xl mx-auto">
          I embrace the journey of creative problem-solving. I’m curious, explorative, and ready to tackle new ideas. Whether it’s through research, design, or art, I like to unwrap fresh solutions and push boundaries. I’m also creative, empathetic, fast, and always up for a good laugh — let’s break free and create something amazing together!
        </p>
      </div>
    </section>
  </template>
  
  <script>
  export default {
  name: "IllustrationsSection",
  mounted() {
    // Create an intersection observer to add 'visible' class on scroll
    const observer = new IntersectionObserver(this.handleIntersection, { threshold: 0.1 });

    this.$nextTick(() => {
      // Select all images in the illustrations section
      const illustrations = this.$el.querySelectorAll('.illustration-image');
      illustrations.forEach(img => {
        observer.observe(img); // Observe each image
      });
    });
  },
  methods: {
    handleIntersection(entries) {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible'); // Add 'visible' class when image is in view
        }
      });
    },
  },
};
  </script>
  
  <style scoped>
  
  /* Scaling effect on hover */
.illustration-image img {
  width: 100%;
  height: auto;
  object-fit: cover;
  transition: transform 0.3s ease, opacity 0.3s ease; /* Smooth transition for scaling and opacity */
}

.illustration-image img:hover {
  transform: scale(1.05); /* Slightly scale the image on hover */
}

/* Fade-in effect */
.illustration-image {
  opacity: 0;
  transition: opacity 1s ease-out; /* Fade-in transition */
}

.illustration-image.visible {
  opacity: 1;
}

/* Grid Layout */
.illustrations-container {
  display: grid;
  grid-template-columns: repeat(1, 1fr); /* Default 1 column on small screens */
  gap: 24px; /* Spacing between images */
}

.illustration-image.col-span-2 {
  grid-column: span 2;
}

/* Responsive design for grid */
@media (min-width: 768px) {
  .illustrations-container {
    grid-template-columns: repeat(2, 1fr); /* 2 columns on medium screens */
  }
}


@media (min-width: 1024px) {


  .illustrations-container {
    grid-template-columns: repeat(3, 1fr); /* 3 columns on large screens */
  }
}

/* Text below images */
.text-container {
  text-align: center;
}

.text-container h3 {
  font-size: 2rem;
  font-weight: bold;
  color: #333;
}

.text-container p {
  font-size: 1.125rem;
  color: #666;
  line-height: 1.5;
  margin-top: 1rem;
}

.text-container button {
  background-color: #1e3a8a;
  color: #fff;
  padding: 10px 20px;
  font-size: 1rem;
  border-radius: 25px;
  border: none;
  cursor: pointer;
}

.text-container button:hover {
  background-color: #0f266d;
}

  </style>
  