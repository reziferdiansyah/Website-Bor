<template>
    <div class="footer">© Developed by {{ DummyDataName }}</div>
</template>


<script>
export default {
  data() {
    return {
      DummyDataName: 'Rezi Ferdiansyah',
    };
  },
};
</script>

<style scoped>
.footer {
   position: fixed;
   left: 0;
   bottom: 0;
   width: 100%;
   background: #333;
   color: white;
   text-align: center;
   padding: 10px;
}
</style>