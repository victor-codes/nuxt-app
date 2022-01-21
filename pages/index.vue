<template>
  <div>
    <h1 class="heading_1">Motion</h1>
    <div class="container">
      <NuxtLink
        v-for="(image, index) in images"
        :to="`image/${index}`"
        :key="image.name"
        class="mask"
      >
        <img
          :key="image.name"
          :src="getImageUrl(image.path)"
          :alt="image.name"
        />
      </NuxtLink>
    </div>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "Motion",
    };
  },
  data() {
    return {
      name: [
        "Woman Looking Sideways in Grayscale Photo",
        "A Girl Posing while Wearing a Bucket Hat on the Field",
        "Woman Wearing Black Dress",
      ],
      images: [
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
      ],
    };
  },
  methods: {
    getImageUrl(path) {
      return `https://images.pexels.com/${path}?auto=format&fit=crop&w=1500`;
    },
  },
};
</script>
