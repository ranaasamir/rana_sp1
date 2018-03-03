<template>
    <div class="row">
      <div class="col-md-12">
        <div class="card">
          <paper-table :title="table1.title" :sub-title="table1.subTitle" :data="table1.data" :columns="table1.columns">

          </paper-table>
        </div>
      </div>

      <div class="actions">
                      <select name="myproducts" class="muproducts">
                          <option value="0" selected="selected">iPhone X</option>
                         <option value="collection">Macbook pro</option>
                         <option value="first-class">iPhone charger</option>
                      </select>
                      <button class="Edit">
                        <slot>Edit</slot>
                      </button>
                      <button class="Delete">
                        <slot>Delete</slot>
                      </button>
                    </div>


        <div class="Search">
        <input type="text" placeholder="Search..">
        </div>

        <div class="Search1">
          <button class="Add">
          <slot>Search</slot>
          </button>
        </div>


        <div class="info">
          <input type="text" v-model="name" placeholder="Product name">
          </div>

          <div class="info1">
          <input type="text" v-model="price" placeholder="Product price">
          </div>

          <div class="info2">
          <input type="text" v-model="createdAt" placeholder="Date of creation">
          </div>

          <div class="info3">
          <input type="text" v-model="updatedAt" placeholder="Date of update">
          </div>

        <form role="form" class="" @submit.prevent="createProduct">
                    <div align="center" style="max-width:400px" class="form-group">
                        <br>
                        <v-card class="grey lighten-4 elevation-0">
                          <v-card-text>
                            <v-container fluid>
                             <v-layout row>
                                 <v-flex xs4>
                                  <v-subheader></v-subheader>
                                </v-flex>
                                <v-flex xs8 style="margin:auto;max-width:100%">
                                  <v-text-field
                                    name="productname"
                                    label="productname"
                                    class="input-group--focused"
                                    placeholder=""
                                    v-validate="{ rules: { required: true} }"
                                    type="text"
                                    v-model="name"
                                    required='true'
                                    id=""
                                  ></v-text-field>
                                </v-flex>
                              </v-layout>
                              </v-container>
                          </v-card-text>
                        </v-card>

                        </div>
                    <div>
                        <div style="max-width:200px">
                            <button class="btn btn-primary btn-sm" style="height:30px">create your product</button>
                        </div>
                    </div>
                </form>




<div class="wrap cf">
  <h1 class="projTitle">Your Shopping Cart</h1>
  <div class="heading cf">
    <h1>Here Are Your chosen Products</h1>
  </div>

  <button class="Add">
  <slot>Add Products</slot>
  </button>

  <div class="cart">
<!--    <ul class="tableHead">
      <li class="prodHeader">Product</li>
      <li>Quantity</li>
      <li>Total</li>
       <li>Remove</li>
    </ul>-->
    <ul class="cartWrap">
      <li class="items odd">

    <div class="infoWrap">
        <div class="cartSection">
        <img src="https://static.highsnobiety.com/wp-content/uploads/2017/11/03175147/favorite-phone-x-accessories-buy-online-01-960x640.jpg" alt="" class="itemImg" />
          <p class="itemNumber"></p>
          <h3>iPhone X</h3>

           <p> <input type="text"  class="qty" placeholder="Quantity"/> x $500.00</p>

          <p class="stockStatus"> In Stock</p>
        </div>


        <div class="prodTotal cartSection">
          <p>$500.00</p>
        </div>

              <div class="cartSection removeWrap">
           <a href="#" class="remove"></a>
        </div>
      </div>
      </li>

            <li class="items odd">
             <div class="infoWrap">
        <div class="cartSection">

        <img src="https://cdn.macrumors.com/article-new/2013/09/macbookpronotouchbar.jpg" alt="" class="itemImg" />
          <p class="itemNumber"></p>
          <h3>Macbook Pro</h3>

           <p> <input type="text"  class="qty" placeholder="Quantity"/> x $1000.00</p>

          <p class="stockStatus out">InStock</p>
        </div>

        <div class="prodTotal cartSection">
          <p>$1000.00</p>
        </div>

            <div class="cartSection removeWrap">
           <a href="#" class="remove">+</a>
        </div>
         </div>
         <div class="special"><div class="specialContent">Free gift with purchase!!</div></div>
      </li>

      <!--<li class="items even">Item 2</li>-->

    </ul>
  </div>

  <div class="promoCode"><label for="promo">Have A Promo Code?</label><input type="text" name="promo" placholder="Enter Code" />
  <a href="#" class="btn"></a></div>

  <div class="subtotal cf">
    <ul>
      <li class="totalRow"><span class="label">Subtotal</span><span class="value">$1500.00</span></li>

          <li class="totalRow"><span class="label">Shipping</span><span class="value">$15.00</span></li>

            <li class="totalRow"><span class="label">Tax</span><span class="value">$10.00</span></li>
            <li class="totalRow final"><span class="label">Total</span><span class="value">$1525.00</span></li>
      <li class="totalRow"><a href="#" class="btn continue">Checkout</a></li>
    </ul>
  </div>
</div>


    </div>
</template>
<script>
  import PaperTable from 'components/UIComponents/PaperTable.vue'
  import axios from 'axios'

  const tableColumns = ['Id', 'Name', 'Price', 'CreatedAt', 'UpdatedAt', 'SellerName']
  const tableData = [{
    id: 1,
    name: 'iPhone X',
    price: '$500.00',
    createdat: '15/2/2018',
    updatedat: '16/2/2018',
    sellername: 'Rana Samir'
  },
  {
    id: 2,
    name: 'Macbook Pro',
    price: '$1000.00',
    createdat: '17/2/2018',
    updatedat: '20/2/2018',
    sellername: 'Rana Samir'
  },
  {
    id: 3,
    name: 'iPhone charger',
    price: '$36.738',
    createdat: '20/2/2018',
    updatedat: '22/2/2018',
    sellername: 'Rana Samir'
  }]

  export default {

    components: {
      PaperTable
    },
    data () {
      return {
        table1: {
          title: 'My store',
          subTitle: 'Our products are the best',
          columns: [...tableColumns],
          data: [...tableData]
        },
        table2: {
          title: 'Table on Plain Background',
          subTitle: 'Here is a subtitle for this table',
          columns: [...tableColumns],
          data: [...tableData]
        },
        name: '',
        price: '',
        createdAt: '',
        updatedAt: ''
      }
    },
    methods: {
      createProduct: function () {
        axios.post('localhost:3000/api/product/createProduct',
          {
            'name': this.name,
            'price': this.price,
            'createdAt': this.createdAt,
            'updatedAt': this.updatedAt
          })
          .then(response => {})
          .catch(e => {
            this.errors.push(e)
          })
        console.log(this.name)
        console.log(this.price)
        console.log(this.createdAt)
        console.log(this.updatedAt)
      }
    }
  }

</script>
<style>

</style>
