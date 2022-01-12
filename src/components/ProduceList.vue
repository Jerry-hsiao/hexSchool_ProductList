<template>
  <div class="app">
    <div class="container">
      <div class="row py-3">
        <div class="col-md-6">
          <h2>產品列表</h2>
          <table class="table table-hover mt-4">
            <caption>
              目前有
              {{
                products.length
              }}
              項產品
            </caption>
            <thead>
              <tr>
                <th scope="col">產品名稱</th>
                <th scope="col">原價</th>
                <th scope="col">售價</th>
                <th scope="col">是否啟用</th>
                <th scope="col">查看細節</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(item, index) in products" :key="index">
                <td>{{ item.name }}</td>
                <td>{{ item.originPrice }}</td>
                <td>{{ item.sellPrice }}</td>
                <td>
                  <span v-if="item.enable" class="text-success">啟用</span>
                  <span v-else>停用</span>
                </td>
                <td>
                  <button
                    type="button"
                    class="btn btn-primary"
                    @click="tempProduct = item"
                  >
                    查看細節
                  </button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
        <div class="col-md-6">
          <h2>單一產品細節</h2>
          <div v-if="tempProduct.name">
            <div class="card mb-4">
              <img
                class="card-img-top primary-image"
                :src="tempProduct.imageUrl"
                alt="Card image cap"
              />
              <div class="card-body">
                <h5 class="card-text">
                  {{ tempProduct.name }}
                  <span class="badge bg-primary ms-2"
                    >{{ tempProduct.category }}
                  </span>
                </h5>

                <p class="card-text">
                  商品描述 :
                  {{ tempProduct.description }}
                </p>
                <p class="card-text">
                  商品內容 :
                  {{ tempProduct.content }}
                </p>
                <p class="card-text">
                  {{ tempProduct.sellPrice }}
                  <del>{{ tempProduct.originPrice }}</del>
                  個 / 元
                </p>
              </div>
            </div>
            <span v-for="(item, index) in tempProduct.imagesUrl" :key="index">
              <img :src="item" alt="" class="images m-2" style="float: left" />
            </span>
          </div>
          <p v-else>請選擇一個商品查看</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductList",
  data() {
    return {
      products: [
        {
          name: "草莓莓果夾心圈",
          originPrice: 150,
          sellPrice: 99,
          enable: true,
          category: "甜甜圈",
          description:
            "濃郁的草莓風味，中心填入滑順不膩口的卡士達內餡，帶來滿滿幸福感!",
          content: "尺寸 : 14x14cm",
          imageUrl:
            "https://images.unsplash.com/photo-1583182332473-b31ba08929c8?ixid=MnwxMjA3fDB8MHxzZWFyY2h8NzR8fGRvbnV0fGVufDB8fDB8fA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=700&q=60",
          imagesUrl: [
            "https://images.unsplash.com/photo-1626094309830-abbb0c99da4a?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2832&q=80",
            "https://images.unsplash.com/photo-1559656914-a30970c1affd?ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTY0fHxkb251dHxlbnwwfHwwfHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=700&q=60",
          ],
        },
        {
          name: "蜂蜜檸檬蛋糕",
          originPrice: 1000,
          sellPrice: 900,
          enable: true,
          category: "蛋糕",
          description:
            "蜜蜂蜜蛋糕，夾層夾上酸酸甜甜的檸檬餡，清爽可口的滋味讓人口水直流!",
          content: "尺寸 : 6寸",
          imageUrl:
            "https://images.unsplash.com/photo-1627834377411-8da5f4f09de8?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1001&q=80",
          imagesUrl: [
            "https://images.unsplash.com/photo-1618888007540-2bdead974bbb?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=987&q=80",
          ],
        },
        {
          name: "暗黑千層",
          originPrice: 700,
          sellPrice: 600,
          enable: true,
          category: "蛋糕",
          description: "法式煎薄餅加上濃郁可可醬，呈現經典的美味及口感。",
          content: "尺寸 : 6寸",
          imageUrl:
            "https://images.unsplash.com/photo-1505253149613-112d21d9f6a9?ixid=MnwxMjA3fDB8MHxzZWFyY2h8NDZ8fGNha2V8ZW58MHx8MHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=700&q=60",
          imagesUrl: [
            "https://images.unsplash.com/flagged/photo-1557234985-425e10c9d7f1?ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTA5fHxjYWtlfGVufDB8fDB8fA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=700&q=60",
            "https://images.unsplash.com/photo-1540337706094-da10342c93d8?ixid=MnwxMjA3fDB8MHxzZWFyY2h8NDR8fGNha2V8ZW58MHx8MHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=700&q=60",
          ],
        },
      ],
      tempProduct: {},
    };
  },
};
</script>

<style scoped>
h2,
h5,
table,
p {
  text-align: left;
}

img {
  object-fit: contain;
  max-width: 100%;
}

.primary-image {
  height: 300px;
}

.images {
  height: 150px;
}
</style>
