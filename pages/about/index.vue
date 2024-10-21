<template>
  <div class="wrap-about">
    <div class="grid-container">
    <h1>The story behind</h1>
    <div>{{ fetchStaticDataStory }}</div>
    <h1>VISI</h1>
    <div>{{ fetchStaticDataVisi }}</div>
    <h1>MISI</h1>  
    <div>
      <li v-for="datas in fetchStaticDataMisi">
        {{ datas.description }}
     </li>
  </div>
</div></div>
</template>

<script>
definePageMeta({
   layout: 'homepage'
})

export default {
    data() {
      const staticMisi = [
        {
          id: 1,
          description : "Investing in developing products with character and paying attention to the criteria to be the best.",
        },
        {
          id: 2,
          description : "Reading franchise systems, e-commerce.",
        },
        {
          id: 3,
          description : "Expanding the scope of theme product criteria, to technical, lifestyle.",
        },
        {
          id: 4,
          description : "Expanding product marketing in showrooms and online.",
        },
        {
          id: 5,
          description : "Providing quality and satisfying products for customer needs.",
        },
        {
          id: 6,
          description : "Lorem Ipsum is simply dummy text of the printing and typesetting industry.",
        },
      ];
      return {
        fetchStaticDataMisi: staticMisi,
        fetchStaticDataVisi : 'Becoming a global product in products, especially lifestyle. Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industrys standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.',
        fetchStaticDataStory : 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industrys standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.'
        
      };
    },
  };
</script>

<style scoped>
.wrap-about {
    padding: 35px;
    overflow-y: scroll;
    margin-bottom: 50px;
}
.grid-container {
  display: grid;
  gap: 50px;
  grid-template-columns: auto auto;
}

/* Desktop Version */
@media (max-width: 768px) {
   .grid-container {
      grid-template-columns: auto auto;
      gap: 50px;
    }
  }
  /* Mobile Version */
  @media (max-width: 480px) {
    .grid-container {
      grid-template-columns: auto;
      gap: 20px;
    }
  }
</style>
