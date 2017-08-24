<template lang="html">
  <section class="bucket-list-items grid">
    <div v-if="!buckets" class="table-head">
      Create a Bucket to Get Started
    </div>
    <div class="grid-table">
      <div class="table-head">Bucket</div>
      <div class="table-head">Name</div>
      <div class="table-head">Storage</div>
      <div class="table-head">Transfer</div>
      <div class="table-head">Status</div>
      <div class="table-body bucket-icon hidden-xs">
        <img src="../../../../static/img/icon-bucket.svg" alt="">
      </div>
      <div class="table-body bucket-label">
        <a @click="navigateToBucket">{{ bucket.name }}</a>
      </div>
      <div class="table-body bucket-storage">{{ bucket.storage }} GB</div>
      <div class="table-body bucket-transfer">{{ bucket.transfer }} GB</div>
      <div class="table-body bucket-status">{{ bucket.status }}</div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'bucket-list-items',

  props: [ 'buckets' ],

  methods: {
    navigateToBucket (bucketId) {
      this.$router.push({
        name: 'Bucket Files', params: { bucketId: bucketId }
      });
    }
  }
};
</script>

<style lang="scss" scoped>
  .table {
    margin-bottom: 0;
  }

  tbody a {
  	cursor: pointer;
  }

  tr {
    -webkit-transition: all 0.15s ease-in-out;
    -moz-transition: all 0.15s ease-in-out;
    -ms-transition: all 0.15s ease-in-out;
    transition: all 0.15s ease-in-out;
  }

  th, td {
    padding: 1.8em !important;
  }

  .table>thead>tr>th {
    border-bottom: 1px solid #eee;
  }

  .table>thead>tr>th,
  .table>tbody>tr>th,
  .table>tfoot>tr>th,
  .table>thead>tr>td,
  .table>tbody>tr>td,
  .table>tfoot>tr>td {
      border-top: 1px solid #eee;
  }

  .bucket-icon {
    padding: 22px 0 0 26px !important;
    margin: 0;
    width: 70px;
  }

  .bucket-icon img {
    width: 42px;
    padding: 0;
    margin: 0;
  }

  .clickable-row {
    cursor: pointer;
  }
</style>
