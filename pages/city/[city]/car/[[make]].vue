<script setup>
const route = useRoute();
const {data: cars, refresh} = await useFetchCars(route.params.city, {
  minPrice: route.query.minPrice,
  maxPrice: route.query.maxPrice,
  make: route.params.make,
});
watch(() => route.query, () => {
  //refresh();
  window.location.reload(true); // dirty hack
});
</script>

<template>
  <div>
    <CarCards v-if="cars.length" :cars="cars" />
    <div v-else class="text-red-600">
      <h1>No cars with filters</h1>
    </div>
  </div>
</template>
