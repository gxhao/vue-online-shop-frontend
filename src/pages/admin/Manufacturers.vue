<template>
  <div class="manufacturers">
    <el-table
    class="table"
    :data="manufacturers">
      <el-table-column
        prop="name"
        label="制造商"
        width="180">
      </el-table-column>
      <el-table-column
        label="操作"
        width="200">
        <template slot-scope="scope">
          <el-button class="modify" type="text" size="small"><router-link :to="'/admin/manufacturers/edit/' + scope.row._id">修改</router-link></el-button>
          <el-button class="remove" @click="removeManufacturer(scope.row._id), deleteRow(scope.$index, products)" type="text" size="small">删除</el-button>
        </template>
      </el-table-column>
    </el-table>
    // ...
  </div>
</template>

<style>
.manufacturers {
  padding-top: 20px;
  text-align: center;
}
.table {
  margin:0 auto;
  width: 380px;
}
.el-table .cell {
  text-align: center;
  padding-top: 10px;
  padding-bottom: 10px;
}
.modify {
  color: blue;
}

.remove a {
  color: red;
}
</style>
<script>
export default {
  created() {
    this.$store.dispatch('allManufacturers');
  },
  computed: {
    manufacturers() {
      return this.$store.getters.allManufacturers
    }
  },
  methods: {
    removeManufacturer(manufacturerId) {
      // 使用 JavaScript BOM 的 confirm 方法来询问用户是否删除此制造商
      const res = confirm('是否删除此制造商？');

      // 如果用户同意，那么就删除此制造商
      if (res) {
        this.$store.dispatch('removeManufacturer', {
          manufacturerId,
        })
      }
    }
  }
}
</script>
