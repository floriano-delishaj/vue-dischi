<template>
  <div>
    <!-- GENRES -->
    <select
      v-model="selectedGenre"
      @change="$emit('selectGenre', selectedGenre)"
    >
      <option disabled value="">Please choice genre</option>
      <option value="">All</option>
      <option v-for="(genre, i) in genres" :key="i" :value="genre">
        {{ genre }}
      </option>
    </select>

    <select
      v-model="selectedArtist"
      @change="$emit('selectAuthor', selectedArtist)"
    >
      <option disable value="">Please choice artist</option>
      <option value="">All</option>
      <option v-for="(artist, i) in artists" :key="i" :value="artist">
        {{ artist }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedGenre: "",
      selectedArtist: "",
    };
  },
  props: {
    genres: Array,
    artists: Array,
  },
};
</script>

<style lang="scss" scoped>
</style>