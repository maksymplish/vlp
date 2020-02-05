<template>
  <nav aria-label="Pagination">
    <ul class="pagination">
      <li class="current">
        <span class="show-for-sr">You're on page</span> 1
      </li>
      <li v-for="pageNumber in pages">
        <a href="#" aria-label="Page">{{pageNumber}}</a>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  props: ["totalPages"],
  data() {
    return {};
  },
  computed: {
    pages() {
      let pagesArr = [];
      for (let index = 1; index <= this.totalPages; index++) {
        pagesArr.push(index);
      }
      return pagesArr;
    }
  }
};
</script>