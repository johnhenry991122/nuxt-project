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
.nav-appbar {
  .mu-appbar-title {
    line-height: 1;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    color: rgba(0, 0, 0, .54);
    > img {
      width: 36px;
      height: 36px;
      margin-right: 8px;
    }
  }
}
.page {
  padding-left: 256px;
  &.is-collapse {
    padding-left: 56px;
  }
}
.page-header {
  position: fixed;
  left: 256px;
  top: 0;
  right: 0;
  transition: all .45s cubic-bezier(0.23, 1, 0.32, 1);
  .page.is-collapse & {
    left: 56px;
  }
}
.nuxt-link-exact-active {
  .mu-item-action {
    color: #2196f3;
  }
  .mu-item {
    color: #2196f3;
  }
}
.page-side-bar {
  width: 256px;
  transition: all .45s cubic-bezier(0.23, 1, 0.32, 1);
  .page.is-collapse & {
    width: 56px;
  }
}
</style>
