<template>
  <div class="home">
    <Header msg="Web Component / Vue JS Admin UI Demo"/>
    <mdb-container>
      <mdb-row>
        <mdb-col col="3">
          <LeftPanel
          />
        </mdb-col>
        <mdb-col col="6">
          <MainPanel
            :title = title
            :url = url
            @select="handleSelect"
          />
        </mdb-col>
        <mdb-col col="3">
          <RightPanel
            :title = title
            :detail = detail
          />
        </mdb-col>
      </mdb-row>
    </mdb-container>
  </div>
</template>

<script>
// @ is an alias to /src
import {
  mdbContainer,
  mdbRow,
  mdbCol
} from "mdbvue";
import Header from '@/components/Header.vue'
import LeftPanel from '@/components/LeftPanel.vue'
import MainPanel from '@/components/MainPanel.vue'
import RightPanel from '@/components/RightPanel.vue'

export default {
  name: 'home',
  components: {
    mdbContainer,
    mdbRow,
    mdbCol,
    Header,
    LeftPanel,
    MainPanel,
    RightPanel
  },
  data() {
    return {
      title : 'Posts',
      url: 'https://jsonplaceholder.typicode.com/posts',
      detail: {}
    };
  },
  methods: {
    handleSelect(detail) {
      this.detail = detail
    }
  }
}
</script>
