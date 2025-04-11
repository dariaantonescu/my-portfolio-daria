<template>
  <div class="about-container">
    <section class="intro-section py-16 px-8">
      <!-- Left side: text content -->
      <div class="text-content w-full md:w-1/2 pr-8 text-left">
        <p class="mt-4 text-lg text-gray-700">A little intro</p>
        <h3 class="mt-4 text-3xl text-gray-900">My name is Daria, and I’m a Multimedia Design student.</h3>
        <p class="mt-8 text-lg text-gray-600 max-w-3xl mx-auto">
          I am continuously expanding my skill set in both visual design and web development. I like to create user-centered visual products that inspire and make a meaningful impact. I see design as a powerful tool for connection, storytelling, and driving understanding of important topics.
        </p>
      </div>

      <!-- Right side: video and buttons -->
      <div class="video-container w-full md:w-1/2 bg-white p-8 rounded-lg mt-8 md:mt-0">
        <iframe
          width="100%" height="315"
          src="https://www.youtube.com/embed/2hTFOzZlwqU"
          frameborder="0"
          allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen>
        </iframe>
        <div class="mt-6 flex flex-col justify-center gap-4">
          <!-- Video CV -->
          <a href="https://www.youtube.com/embed/2hTFOzZlwqU" target="_blank">
            <button class="bg-blue-800 text-blue-950 px-8 py-3 rounded-md w-full max-w-xs text-center">
              Video CV
            </button>
          </a>

          <!-- Download CV -->
          <a href="/visuals/CV_DariaAntonescu_.pdf" download>
            <button class="bg-gray-300 text-blue-950 px-8 py-3 rounded-md w-full max-w-xs text-center">
              Download CV
            </button>
          </a>
        </div>
      </div>
    </section>

    <!-- Competences section -->
    <section id="competences" class="competences-section mt-16">
      <div class="competences-container flex">
        <!-- Competences Title -->
        <div class="competences-title p-8">
          <h2 class="text-3xl font-bold text-blue-950">Competences</h2>
        </div>

        <div class="competences-content w-full pl-8">
          <div
            v-for="(competence, index) in competences"
            :key="index"
            class="competence-item mt-8 opacity-0 transition-opacity duration-1000 ease-out"
            :class="{'fade-in': competence.show}">
            <h3 class="text-2xl font-semibold text-gray-800">{{ competence.title }}</h3>
            <p class="mt-4 text-lg text-gray-600">{{ competence.description }}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "About",
  data() {
    return {
      competences: [
        {
          title: "Adobe Creative Suite",
          description:
            "I possess skills in InDesign, Illustrator, and Photoshop, with hands-on experience in creating professional designs across various media.",
          show: false,
        },
        {
          title: "Illustration",
          description:
            "I have a personal passion for creating illustrations for businesses, family, and friends. I love to illustrate whenever I get the chance.",
          show: false,
        },
        {
          title: "Visual Identity",
          description:
            "Strong design isn’t just about aesthetics, it also needs a solid strategic foundation. I’ve developed a better understanding of strategic marketing and UX research.",
          show: false,
        },
        {
          title: "Print",
          description:
            "I have a deep appreciation for typography and have gained knowledge in layout design through poster, brochures, and booklet design projects over the years.",
          show: false,
        },
        {
          title: "Image & Video",
          description:
            "I have a strong interest in photography and videography. Whether for personal projects or professional use, I enjoy capturing moments that enhance visual narratives.",
          show: false,
        },
      ],
    };
  },
  mounted() {
    const options = {
      root: null,
      threshold: 0.1,
    };
    const observer = new IntersectionObserver(this.handleIntersection, options);
    this.$nextTick(() => {
      const competenceItems = this.$el.querySelectorAll('.competence-item');
      competenceItems.forEach(item => observer.observe(item));
    });
  },
  methods: {
    handleIntersection(entries) {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('fade-in');
          entry.target.classList.remove('opacity-0');
        }
      });
    },
  },
};
</script>

<style scoped>
.about-container {
  padding: 2rem;
}

.intro-section {
  display: flex;
  justify-content: flex-start; 
  align-items: flex-start; 
  flex-wrap: wrap; 
  text-align: left; 
}

.text-content {
  max-width: 100%; 
}

.text-container p {
  max-width: 100%; 
  margin-top: 1rem; 
  text-align: left; 
}

.video-container {
  background-color: white;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  margin-top: 2rem;
}

.video-container iframe {
  width: 100%;
  height: 315px;
}

.competences-section {
  padding: 3rem;
}

.competences-container {
  display: flex;
  width: 100%;
  flex-wrap: wrap; /* Allow flex container to wrap */
}

.competences-title {
  text-align: left;
}

.competences-content {
  width: 100%;
  padding-left: 3rem;
  text-align: left;
}

.competence-item {
  padding: 1rem;
  border-bottom: 1px solid #e5e7eb;
  opacity: 0;
  transition: opacity 0.3s ease-out;
}

@keyframes fadeInUp {
  0% {
    opacity: 0;
    transform: translateY(20px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in {
  animation: fadeInUp 0.8s ease-out forwards;
}

@media (max-width: 768px) {
  .intro-section {
    flex-direction: column;
    align-items: left;
    padding-left: 0;  /* Remove padding */
    padding-right: 0; /* Remove padding */
  }

  .about-container {
    padding: 0rem;
  }

  .video-container {
    padding: 0rem;
    width: 100%;
    margin-top: 2rem;
  }

  .video-container iframe {
    width: 100%;
    height: 315px;
  }

  .competences-container {
    flex-direction: column;
    padding-left: 0;
  }

  .competences-section {
    padding: 0rem;
  }

  .competences-title {
    width: 100%;
    padding: 1rem;
    font-size: 2rem;
    text-align: left;
    margin-bottom: 1rem;
  }

  .competences-content {
    width: 100%;
    padding-left: 0;
  }

  .competence-item {
    padding: 1rem;
    border-bottom: 1px solid #e5e7eb;
    opacity: 0;
    transition: opacity 0.3s ease-out;
    margin-bottom: 20px;
  }

  .competence-item h3 {
    font-size: 1.5rem;
    margin-bottom: 1rem;
  }

  .competence-item p {
    font-size: 1rem;
    line-height: 1.5;
  }
}
</style>