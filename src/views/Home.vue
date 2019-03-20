<template>
  <section>
    <div class="container" >
      <h1>Are You Bored</h1>
      <p>Let's help you get something to do to make you less bored</p>
      <div class="control">
        <ui-select
          placeholder="Select an activity"
          :options="list"
          v-model="activity"
        >
        </ui-select>
        <ui-button
          raised
          :size="size"
          color="primary"
          @click="getActivity"
        >
          <i class="fas fa-search"></i>
        </ui-button>
      </div>
      <ui-progress-circular
        color="multi-color"
        v-if="loading"
      >
      </ui-progress-circular>
      <div v-else class="body">
        <div v-if="activities != null" class="card">
          <h3>{{ activities.activity }}</h3>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import axios from 'axios'
export default {
  name: 'home',
  data () {
    return {
      loading: false,
      size: 'normal',
      activity: 'Recreational',
      list: [
        'Education',
        'Recreational',
        'Social',
        'Diy',
        'Charity',
        'Cooking',
        'Relaxation',
        'Music',
        'Busywork'
      ],
      activities: null
    }
  },
  methods: {
    getActivity () {
      this.loading = true
      const proxyUrl = 'https://cors-anywhere.herokuapp.com/'
      axios.get(proxyUrl + `https://www.boredapi.com/api/activity?type=${this.activity.toLowerCase()}`)
        .then(res => {
          this.loading = false
          this.activities = res.data
        })
        .catch(error => {
          this.loading = false
          console.log(error)
        })
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/mixins.scss";
section {
  text-align: center;
  margin: 10% auto 0 auto;
  h1 {
    color: color(text-primary);
  }
  p {
    color: color(text-secondary);
    line-height: 1.5em;
  }
  .container {
    width: 80%;
    margin: auto;
    @include medium {
      width: 60%;
    }
    @include tablet {
      width: 40%;
    }
    .control {
      display: flex;
      .ui-select {
        flex: 3;
        margin-right: 1em;
      }
      .ui-button {
        flex: 1;
      }
    }
    .card {
      padding: 1em;
      background-color: white;
      box-shadow: $shadow;
      border-radius: 8px;
      h3 {
        line-height: 1.6em;
        color: color(text-primary);
      }
    }
    .ui-progress-circular {
      margin: 3em auto;
    }
  }
}
</style>
