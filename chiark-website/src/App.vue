<template>
  <div id="app">
    <div class="tabs">
      <div v-for="(tab, index) in tabs" :key="index" :class="['tab', { active: activeTab === tab }]" @click="setActiveTab(tab)">
        {{ tab.name }}
      </div>
    </div>
    <div class="tab-content">
      <component :is="activeTab.component" />
    </div>
    <div class="arrows">
      <div class="arrow left" @click="prevTab">
        <i class="fa fa-arrow-left"></i>
      </div>
      <div class="arrow right" @click="nextTab">
        <i class="fa fa-arrow-right"></i>
      </div>
    </div>
  </div>
</template>

<script>
import TabOne from './TabOne.vue';
import TabTwo from './TabTwo.vue';
import TabThree from './TabThree.vue';
import TabFour from './TabFour.vue';
import TabFive from './TabFive.vue';

export default {
  name: 'App',
  data() {
    return {
      activeTab: {},
      tabs: [
        {
          name: 'Tab 1',
          component: TabOne
        },
        {
          name: 'Tab 2',
          component: TabTwo
        },
        {
          name: 'Tab 3',
          component: TabThree
        },
        {
          name: 'Tab 4',
          component: TabFour
        },
        {
          name: 'Tab 5',
          component: TabFive
        }
      ]
    }
  },
  methods: {
    setActiveTab(tab) {
      this.activeTab = tab;
    },
    nextTab() {
      const nextIndex = this.tabs.indexOf(this.activeTab) + 1;
      if (nextIndex < this.tabs.length) {
        this.activeTab = this.tabs[nextIndex];
      }
    },
    prevTab() {
      const prevIndex = this.tabs.indexOf(this.activeTab) - 1;
      if (prevIndex >= 0) {
        this.activeTab = this.tabs[prevIndex];
      }
    }
  },
  mounted() {
    this.activeTab = this.tabs[0];
  }
}
</script>

<style>
.tabs {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
}

.tab {
  padding: 10px 20px;
  cursor: pointer;
}

.active {
  color: red;
}

.arrow {
  padding: 10px 20px;
  cursor: pointer;
}

.fa-arrow-left,
.fa-arrow-right {
  font-size: 20px;
}

.tab-content {
  padding: 20px;
}
</style>
