<template>
  <div>
    <v-card-title>
      <v-btn color="primary" @click="addBrand">新增品牌</v-btn>
      <!--搜索框，与search属性关联-->
      <v-spacer/>
      <v-flex xs3>
        <v-text-field label="输入关键字搜索" v-model.lazy="search" append-icon="search" hide-details/>
      </v-flex>
    </v-card-title>
    <v-divider/>
    <v-data-table
      :headers="headers"
      :items="brands"
      :pagination.sync="pagination"
      :total-items="totalDesserts"
      :loading="loading"
      class="elevation-1"
    >
      <template slot="items" slot-scope="props">
        <tr>
          <td class="text-xs-center">{{ props.item.id }}</td>
          <td class="text-xs-center">{{ props.item.name }}</td>
          <td class="text-xs-center">{{ props.item.image }}</td>
          <td class="text-xs-center">{{ props.item.letter }}</td>
          <td class="text-xs-center">

            <v-btn fab dark small color="cyan">
            <v-icon dark>edit</v-icon>
          </v-btn>
            <v-btn fab dark small color="primary">
              <v-icon dark>remove</v-icon>
            </v-btn>
            </td>
        </tr>
      </template>
    </v-data-table>
  </div>
</template>

<script>
  export default {
    name: "myBrand",
    data() {
      return {
        search:'',
        totalDesserts: 0,
        desserts: [],
        loading: true,
        pagination: {},
        headers: [
          {text: 'id', align: 'center', sortable: true, value: 'id'},
          {text: '品牌名称', align: 'center', sortable: false, value: 'name'},
          {text: '品牌LOGO', align: 'center', sortable: false, value: 'image'},
          {text: '品牌首字母', align: 'center', sortable: true, value: 'letter'},
          {text: '操作', align: 'center'}
        ],
        brands: [
          {id: 1, name: "小米", image: "1.jpg", letter: "X"},
          {id: 2, name: "华为", image: "2.jpg", letter: "H"},
          {id: 3, name: "IPhone", image: "3.jpg", letter: "I"},
          {id: 4, name: "中兴", image: "4.jpg", letter: "Z"},
          {id: 5, name: "魅族", image: "5.jpg", letter: "M"},
        ]
      }
    }
  }

</script>

<style scoped>

</style>
