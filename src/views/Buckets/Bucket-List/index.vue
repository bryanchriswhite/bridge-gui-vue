<template>
  <section class="bucket-list container">
    <div v-if="loading" class="loading">
      <Sj-loading></Sj-loading>
    </div>
    <div v-else class="grid">
      <h1 class="title grid-header">Buckets</h1>
      <router-link :to="{ name: 'Create Bucket' }" class="grid-button">
        <button class="btn btn-green btn-action float-right">
          Create Bucket
        </button>
      </router-link>
      <Bucket-List-Items :buckets="buckets" class="grid-table">
      </Bucket-List-Items>
    </div>
  </section>
</template>

<script>
import BucketListItems from './Bucket-List-Items';
import SjLoading from '@/components/Sj-Loading';
import { mapActions, mapState } from 'vuex';

export default {
  name: 'bucket-list',

  components: {
    BucketListItems,
    SjLoading
  },

  created () {
    this.getBuckets().then(() => {
      this.loading = false;
    });
  },

  data () {
    return {
      loading: true
    };
  },

  computed: mapState({
    buckets: state => state.buckets.all
  }),

  methods: {
    ...mapActions([ 'getBuckets' ])
  }
};
</script>

<style lang="scss" scoped>
  .loading {
    margin: 5rem auto;
  }
</style>
