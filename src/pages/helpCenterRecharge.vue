<template>
  <q-page class="account-manage">
    <div class="col-12 row layout-page">
      <div class="layout-page-side">
        <!-- side menu -->
        <helpCenterSideBar></helpCenterSideBar>
      </div>
      <div class="layout-page-main">
        <!-- Title bar -->
        <helpCenterTitleBar :title="title"></helpCenterTitleBar>
        <!-- Content -->
        <div class="layout-page-content">
          <div class="help-block" v-html="content"></div>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script>
import httpMixin from 'src/httpMixin';

import helpCenterSideBar from 'components/helpCenterSideBar';
import helpCenterTitleBar from 'components/helpCenterTitleBar';

export default {
  name: 'helpCenterRecharge',
  mixins: [httpMixin],
  data() {
    return {
      title: '充值教程',
      content: '',
    };
  },
  components: {
    helpCenterSideBar,
    helpCenterTitleBar,
  },
  created() {
    this.GethelpCenterContent();
  },
  methods: {
    // TODO: API少了充值教程的code
    async GethelpCenterContent() {
      const res = await this.getCopyright('1', 'BT05');
      if (res) {
        this.content = res.content;
      }
    },
  },
};
</script>

<style lang="stylus" scoped>
</style>
