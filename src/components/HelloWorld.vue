<template>
  <div class="hello">
    <!--<p>Họ và tên: {{name}}</p>
      <p>Tuổi:{{age}}</p> -->
    <!-- <p>Họ và tên:{{data[1].name}}</p>
    <p>Tuổi:{{data[1].Age}}</p> -->

    <ul v-for="(Product,idx) in products" :key="idx">
      <li>{{Product.data().name}}</li>
      <li>{{Product.data().Age}}</li>
      <button @click="deleteProduct()" >Delete</button>
    </ul>

    <input type="text" placeholder="Name" v-model="product.name">
    <input type="number" placeholder="Age" v-model="product.Age">
    <button @click="saveData">Save</button>
  </div>
</template>

<script>
  import db from '../firebase/firebaseInit'
  export default {
    name: 'HelloWorld',
    data() {
      return {
        products: [],
        product:{
          name:null,
          Age:null
        }
      }
    },
    methods: {
      getData() {
        db.collection('Product').get().then(snapshoot => {
          snapshoot.forEach(doc => {
            this.products.push(doc);
          })
        })
      },
      saveData() {
        db.collection("Product").add(this.product)
          .then((docRef) => {
            console.log("Document written with ID: ", docRef.id);
            // this.reset();
          })
          .catch((error) => {
            console.error("Error adding document: ", error);
          });
      },
      reset(){
        Object.assign(this.$data, this.$options.data.apply(this));
      },
      deleteProduct(){

      }
    },
    props: {
      msg: String
    },
    created() {
      this.getData();
    },
    watch: {
      // data(){
      //   this.name = this.datas[0].name;
      //   this.age = this.datas[0].Age;
      //   console.log(this.datas)
      // }
    },
    mounted() {
      console.log(db);
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h3 {
    margin: 40px 0 0;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }
</style>
