<template>
  <mdb-container class="green-text left-panel">
    <mdb-list-group>
      <mdb-nav-item class="list-group-item list-group-item-action" to="/users">
        <h5 class="justify-content-between d-flex align-items-center">
          Users <mdb-icon icon="angle-right"/>
        </h5>
      </mdb-nav-item>

      <mdb-nav-item class="list-group-item list-group-item-action" to="/posts">
        <h5 class="justify-content-between d-flex align-items-center">
          Posts <mdb-icon icon="angle-right"/>
        </h5>
      </mdb-nav-item>
      <mdb-nav-item class="list-group-item list-group-item-action" to="/comments">
        <h5 class="justify-content-between d-flex align-items-center">
          Comments <mdb-icon icon="angle-right"/>
        </h5>
      </mdb-nav-item>
    </mdb-list-group>
  </mdb-container>
</template>

<script>
  import { mdbNavItem, mdbListGroup, mdbContainer, mdbIcon } from 'mdbvue';
  export default {
    name: 'LeftPanel',
    components: {
      mdbListGroup,
      mdbNavItem,
      mdbIcon,
      mdbContainer,
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .container {
    height: 750px;
  }
  .icon-div {
    width: 49%;
    display: inline-block;
  }
  .icon-div .fa {
    cursor: pointer;
  }
</style>
