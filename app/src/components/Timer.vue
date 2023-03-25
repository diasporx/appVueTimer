<template>
  <div class="container py-5 overflow-hidden">
    <div class="row">
      <transition-group name="list">
        <div class="col-md-6 col-12 col-lg-4 d-flex align-items-center justify-content-center p-4 mnH-cols"
          v-for="(stopwatch, index) in stopwatches" :key="index">
          <div :class="`block-timer ${stopwatch.status === 'running' ? 'active_timer' : ''}`">
            <div class="d-flex timer-Main align-items-center justify-content-center thisHeight">
              <span class="mb-0 text-center timerFont">{{ formatTime(stopwatch.time) }}</span>
            </div>
            <div class="d-flex timer-buttons thisHeight align-items-center justify-content-evenly">
              <button @click="startStopwatch(stopwatch)" v-if="stopwatch.status === 'paused'">
                <svg width="40" height="40">
                  <polygon points="12,8 32,20 12,32" fill="#9E9E9E" />
                </svg>
              </button>
              <button @click="pauseStopwatch(stopwatch)" v-if="stopwatch.status === 'running'">
                <svg width="40" height="40" viewBox="0 0 40 40">
                  <rect x="12" y="10" width="5" height="20" fill="#9E9E9E" />
                  <rect x="20" y="10" width="5" height="20" fill="#9E9E9E" />
                </svg>
              </button>
              <button @click="resetStopwatch(stopwatch)">
                <svg width="40" height="40" viewBox="0 0 40 40">
                  <rect x="10" y="10" width="10" height="20" fill="#9E9E9E" />
                  <rect x="20" y="10" width="10" height="20" fill="#9E9E9E" />
                </svg>
              </button>
            </div>
          </div>
        </div>
      </transition-group>
      <div class="col-md-6 col-12 col-lg-4 d-flex align-items-center justify-content-center p-4 mnH-cols">
        <button @click="addStopwatch()">
          <svg width="40" height="40" viewBox="0 0 40 40">
            <rect x="10" y="18" width="20" height="5" fill="#9E9E9E" />
            <rect x="18" y="10" width="5" height="20" fill="#9E9E9E" />
          </svg>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import func from './__include/functions.vue';
export default {
  name: 'Timer',
  mixins: [func],
  data() {
    return {
      stopwatches: [],
      nextId: 1
    }
  }
}
</script>

<style lang="scss" scoped>
$noActive: #9E9E9E;
$Active: #fff;

.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}

button {
  background: transparent;
  outline: none;
  box-shadow: none;
  border: none;
}

.mnH-cols {
  min-height: 168px;
}

.block-timer.active_timer {
  svg {
    rect {
      fill: $Active;
    }
  }

  .timer-Main {
    border-bottom: 1px solid $Active;

    .timerFont {
      color: $Active;
    }
  }
}

.block-timer {
  width: 225px;
  height: 120px;
  background-color: #696969;

  .thisHeight {
    height: 60px;
  }

  .timer-Main {
    border-bottom: 1px solid $noActive;

    .timerFont {
      font-family: 'Gotham';
      font-weight: 700;
      color: $noActive;
    }
  }
}

.block-timer:last-child {
  margin-right: 0;
}
</style>
