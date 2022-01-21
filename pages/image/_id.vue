<template>
  <transition name="fade">
    <div>
      <div class="main">
        <div class="img">
          <img
            class="single_image"
            :src="getImageUrl(image.path)"
            :alt="image.path"
          />
        </div>
        <div class="info">
          <div>
            <h2>{{ image.name }}</h2>
          </div>
          <div class="next_container" style="width: fit-content" v-if="nextId">
            <div class="absolute">
              <img
                class="next_image"
                :src="getNextImageUrl(nextImage.path)"
                :alt="nextImage.name"
              />
            </div>
            <NuxtLink class="next" :to="`${nextId}`"
              >Next <span> ←</span></NuxtLink
            >
          </div>
        </div>
      </div>
      <div class="back">
        <NuxtLink to="/">← Back</NuxtLink>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  head() {
    return {
      title: `${this.image.name} | Motion`,
    };
  },
  async asyncData({ params, redirect }) {
    const { id } = params;
    const images = [
      {
        name: "Woman Looking Sideways in Grayscale Photo",
        path: "photos/1396538/pexels-photo-1396538.jpeg",
      },
      {
        name: "A Girl Posing while Wearing a Bucket Hat on the Field",
        path: "photos/8945169/pexels-photo-8945169.jpeg",
      },
      {
        name: "Woman Wearing Black Dress",
        path: "photos/3050279/pexels-photo-3050279.jpeg",
      },
      {
        name: "Photo of Man Using SIlver Vintage Camera",
        path: "photos/7872628/pexels-photo-7872628.jpeg",
      },
      {
        name: "Woman in Black and White Checked Mini Skirt and Brown Coat",
        path: "photos/3597932/pexels-photo-3597932.jpeg",
      },
      {
        name: "Grayscale Photo of Woman's Face",
        path: "photos/4664273/pexels-photo-4664273.jpeg",
      },
      {
        name: "Woman Wearing Pullover Hoodie",
        path: "photos/3353607/pexels-photo-3353607.jpeg",
      },
    ];
    if (images[id]) {
      const image = images[id];
      const nextImage = images[Number(id) + 1];
      const nextId = nextImage ? Number(id) + 1 : false;
      return {
        image: image,
        currentId: id,
        nextImage: nextImage ? nextImage : false,
        nextId: nextId,
      };
    } else {
      redirect("/");
    }
  },
  methods: {
    getImageUrl(path) {
      return `https://images.pexels.com/${path}?auto=format&fit=crop&w=1500`;
    },
    getNextImageUrl(path) {
      return `https://images.pexels.com/${path}?auto=format&fit=crop&w=200`;
    },
  },
};
</script>
