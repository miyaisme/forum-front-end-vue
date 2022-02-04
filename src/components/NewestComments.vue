<template>
  <div class="card">
    <div class="card-header">
      最新評論
    </div>
    <div 
      v-for="comment in comments" 
      :key="comment.id"
      class="card-body"
    >
      <div>
        <h4>
          <a href="#">
            {{ comment.Restaurant.name }}
          </a>
        </h4>
        <p>{{ comment.text }}</p>by
        <a href="#">
          {{ comment.User.name }}
        </a>
        at
        {{ comment.createdAt | fromNow }}
        <hr>
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  filters: {
    fromNow(datetime) {
      if(!datetime) {
        return '='
      }
      return moment(datetime).fromNow()
    }
  },
  props: {
    comments: {
      type: Array,
      required: true,
    }
  }
}
</script>