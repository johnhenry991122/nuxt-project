<template>
<div class="page" :class="{'is-collapse': collapse}">
  <mu-appbar color="primary" class="page-header" :z-depth="1">
    <mu-button icon slot="left" @click="toggleMenu">
      <mu-icon value="menu"/>
    </mu-button>
    <mu-button icon slot="right" @click="toggleTheme">
      <mu-icon :value="theme === 'light' ? 'lightbulb_outline' : 'lightbulb'" />
    </mu-button>
  </mu-appbar>
  <mu-drawer open docked :z-depth="0" class="page-side-bar">
    <mu-appbar class="nav-appbar" :z-depth="0" color="transparent">
      {{ collapse ? 'M' : 'Muse Template'}}
    </mu-appbar>
    <mu-divider />
    <mu-list>
      <mu-list-item button to="/" active-class="active-link">
        <mu-list-item-action>
          <mu-icon value="apps"/>
        </mu-list-item-action>
        <mu-list-item-title>Welcome</mu-list-item-title>
      </mu-list-item>
      <mu-list-item button to="/about" active-class="active-link">
        <mu-list-item-action>
          <mu-icon value="info"/>
        </mu-list-item-action>
        <mu-list-item-title>About</mu-list-item-title>
      </mu-list-item>
    </mu-list>
  </mu-drawer>
  <nuxt/>
</div>
</template>

<script>
import theme from 'muse-ui/lib/theme';
export default {
  data () {
    return {
      theme: 'light',
      collapse: false
    }
  },
  mounted () {
    theme.use(this.theme);
  },
  methods: {
    toggleTheme () {
      this.theme = this.theme === 'light' ? 'dark' : 'light';
      theme.use(this.theme);
    },
    toggleMenu () {
      this.collapse = !this.collapse;
    }
  }
};
</script>


<style lang="less">

</style>
