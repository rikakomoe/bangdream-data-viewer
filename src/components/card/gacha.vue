<template>
  <div>
    <q-card inline>
      <q-card-title class="bg-pink text-white">
        {{data.gachaName}}
      </q-card-title>
      <q-card-media>
        <img v-lazy="`/assets-${server}/gacha/screen/${data.resourceName}_logo.png`" class="responsive" style="max-height: 140px;" />
      </q-card-media>
      <q-card-main>
        <h5 class="q-my-sm" v-if="Number(data.publishedAt) > Date.now()">{{$t('not-started')}}<br>{{(new Date(Number(data.publishedAt))).toLocaleString()}}</h5>
        <count-down :target-time="Number(data.closedAt)" v-else></count-down>
      </q-card-main>
      <q-card-separator />
      <q-card-actions>
        <q-btn flat class="text-pink"
          @click="$emit('open-modal')"
          icon="launch"
        >{{$t('gacha.open-detail')}}</q-btn>
      </q-card-actions>
    </q-card>
  </div>
</template>

<script>
import CountDown from 'components/common/countdown'

export default {
  // name: 'ComponentName',
  props: ['data', 'server'],
  data () {
    return {
      isGcahaReady: false
    }
  },
  components: {
    CountDown
  }
}
</script>

<style lang="stylus" scoped>
</style>
