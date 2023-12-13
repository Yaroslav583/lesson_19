<template>
  <div>
    <h2>Flex playground</h2>

    <div>
      <h3>justify-content</h3>


      <div>
        <button :class="{ 'active': flexStyles['justify-content'] === 'start' }"
                @click="selectJustifyContent('start')">start
        </button>
        <button :class="{ 'active': flexStyles['justify-content'] === 'center' }"
                @click="selectJustifyContent('center')">center
        </button>
        <button :class="{ 'active': flexStyles['justify-content'] === 'space-between' }"
                @click="selectJustifyContent('space-between')">space-between
        </button>
        <button :class="{ 'active': flexStyles['justify-content'] === 'space-around' }"
                @click="selectJustifyContent('space-around')">space-around
        </button>
      </div>
    </div>

    <div>
      <h3>align-items</h3>

      <div>
        <button :class="{ 'active': flexStyles['align-items'] === 'stretch' }"
                @click="selectAlignItems('stretch')">
          stretch
        </button>
        <button :class="{ 'active': flexStyles['align-items'] === 'center' }"
                @click="selectAlignItems('center')">
          center
        </button>
        <button :class="{ 'active': flexStyles['align-items'] === 'flex-start' }"
                @click="selectAlignItems('flex-start')">start
        </button>
        <button :class="{ 'active': flexStyles['align-items'] === 'flex-end' }"
                @click="selectAlignItems('flex-end')">
          end
        </button>
      </div>
    </div>

    <div>
      <button @click="showCodeBlock = !showCodeBlock">{{ showCodeBlock ? 'Hide code' : 'Show code' }}</button>
      <div v-if="showCodeBlock">
        <pre>{{ ` .flex-box {
  display: flex;
  justify-content: ${flexStyles['justify-content']};
  align-items: ${flexStyles['align-items']};
}` }}</pre>
      </div>
    </div>
    <div class="flex-box" :style="flexStyles">
      <div class="flex-item">One</div>
      <div class="flex-item">Two</div>
      <div class="flex-item">Tree</div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      flexStyles: {
        stat: `
          justify-content: ${this['justify-content']};
          align-items: ${this['align-items']};`,
      },

      showCodeBlock: false,
    };
  },
  methods: {
    selectJustifyContent(value) {
      this.flexStyles['justify-content'] = value;

    },
    selectAlignItems(value) {
      this.flexStyles['align-items'] = value;
    },
  },
};
</script>

<style>
.flex-box {
  display: flex;
  width: 600px;
  height: 300px;
  border: 1px solid #000000;
}

.flex-item {
  width: 100px;
  height: 50px;
  background-color: aqua;
  color: black;
  display: flex;
  align-items: center;
  justify-content: center;
 font-weight: bold;
}

button {
  margin-right: 10px;
}

.active {
  background-color: darkblue;
  color: #fff;
}


</style>
