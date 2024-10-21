<template>
    <!-- LIST  -->
   <div v-if="LisnotDetail" class="wrap-card">
     <div style="text-align: center;">
          <h1 style="text-transform: uppercase;">
            our products
          </h1>
      </div>
      <div class="card-container">
          <div v-for="datas in productsList.data" class="card" @click="goToDetailProducts(datas)">
      <div class="text-content-info">
        <div class="box-images-products"> 
          <img style="width: 100% !important; height: 100% !important;" :src="datas.path" :alt="datas.alt">
        </div>
        <p>
         {{ datas.name }}
        </p>
        <p style="color: #ff4d25;">
         RP : {{ datas.price }}
        </p>
      </div>
          </div>
      </div>
      <!-- DETAIL -->
  </div>

  <!-- DETAIL -->
<div v-else class="wrap-detail">
 <p style="margin-bottom: 20px;"> <a style="text-decoration:underline; cursor: pointer;" @click="gotoHome">Home</a> > Products > Detail </p>
  <!-- CARD CONTENT -->
   <div class="card-wrapper">
    <div class="card-detail">
    <!-- CARD LEFT PREVIES IMAGES -->
    <div class="product-imgs">
    <!-- BIG -->
     <Carousel 
      :autoplay="2000"
      id="gallery"
      :items-to-show="1"
      :wrap-around="true" v-model="currentSlide">
     <Slide v-for="(image, imageIndex) in dataDetailShow.pathdetail" :key="dataDetailShow.id">
       <div class="carousel__item">
          <img  style="width: 320px !important; height: 320px !important;" :alt="dataDetailShow.alt" :src="image" :key="imageIndex" />
        </div>
     </Slide>
    </Carousel>
    <!-- PREVIEW -->
    <Carousel
    id="thumbnails"
    :items-to-show="3"
    :wrap-around="true"
    v-model="currentSlide"
    ref="carousel"
  >
    <Slide v-for="(slideThumbnails, imageIndexDetail) in dataDetailShow.pathdetail" :key="dataDetailShow.id">
      <!-- <div class="carousel__item" @click="slideTo(slideThumbnails.id - 1)"> -->
        <div class="carousel__item">
          <img style="width: 100px !important; height: 100px !important;" :alt="dataDetailShow.alt" :src="slideThumbnails" />
      </div>
    </Slide>
   </Carousel>
   </div>
  <!-- CAROUSEL IMAGES -->
  <!-- CARD RIGHT INFORMATION -->
     <div>
      <div class="name-product">{{ dataDetailShow.name }}</div>
      <div class="product-price">
        <p class="new-price">Price: <span>{{ dataDetailShow.price }}</span></p>
      </div>
      <div class="product-detail">
        <h2>about this item: </h2>
        <p>{{ dataDetailShow.description }}</p>
        <p><b>Color: </b> <span>{{ dataDetailShow.color }}</span></p>
        <p><b>Available</b>: <span>{{ dataDetailShow.available }}</span></p>
        <p><b>Size</b>: <span>{{ dataDetailShow.size }}</span></p>
        <p><b>Category: </b><span>{{ dataDetailShow.category }}</span></p>
        <p><b>Shipping Area: </b> <span>{{ dataDetailShow.shippingArea }}</span></p>
        <p><b>Shipping Fee: </b> <span>{{ dataDetailShow.shippingFee }}</span></p>
      </div>
      <div class="purchase-info">
       Amount : <input type="number" placeholder="Amount" min="0" v-model="AmountData">
       Size : <input type="number" placeholder="Size" min="30" max="50" v-model="SizeData">
       <br>
          <button  @click="alertFuntion" type="button" class="btn">
          Add to Cart <i class="fas fa-shopping-cart"></i>
        </button>
      </div>
    </div>
   </div>
  </div>
</div>
<!-- END DETAIL -->
</template>
  
<script>
import { defineComponent } from 'vue'
import { Carousel, Slide } from 'vue3-carousel'
import 'vue3-carousel/dist/carousel.css'

  export default {
    components: {
      Carousel,
      Slide,
    },
    data() {
      return {
        productsList : '',
        dataDetailShow: null,
        LisnotDetail : true,
        AmountData : 1,
        SizeData : 30,
        currentSlide: 0,
      };
    },
    async mounted() {
      this.productsList = await $fetch('https://dummyjson.com/c/62c5-445c-4235-8500')
    },
    methods: {
      goToDetailProducts(datas) {
        this.dataDetailShow = datas
        this.LisnotDetail = false
      },
      gotoHome(){
        this.LisnotDetail = true
      },
      alertFuntion() {
          const SizeFix = this.SizeData
          const AmoutFix = this.AmountData
          alert(`Amount ${AmoutFix} and Size ${SizeFix} Already add to Cart`);
      },
      slideTo(val) {
         this.currentSlide = val;
      },
    } 
  };
  </script>
  
  <style scoped>
  .box-images-products { 
    background-color: white;
    padding: 20px;
  }
  .text-content-info{
    justify-content: center;
    text-align: center;
  }
  .wrap-card {
    padding: 35px;
    overflow-y: scroll;
    margin-bottom: 50px;
  }
  .card-container {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
  }
  .card {
      flex: 1 1 calc(25% - 20px);
      box-sizing: border-box;
      border: 1.5px solid whitesmoke;
      cursor: pointer;
  }
  .card:hover {
     background-color: whitesmoke;
  }
  /* Desktop Version */
  @media (max-width: 768px) {
      .card {
          flex: 1 1 calc(50% - 20px);
      }
  }
  /* Mobile Version */
  @media (max-width: 480px) {
      .card {
          flex: 1 1 calc(50% - 20px);
      }
  }


  /* DETAIL CSS */
a {
  color: black;
 }
.wrap-detail {
    padding: 35px;
    overflow-y: scroll;
    margin-bottom: 50px;
}
.card-wrapper{
    max-width: 1100px;
    margin: 0 auto;
}
img{
    width: 100%;
    display: block;
}
.img-display{
    overflow: hidden;
}
.img-showcase{
    display: flex;
    width: 100%;
    transition: all 0.5s ease;
}
.img-showcase img{
    min-width: 100%;
}
.img-select{
    display: flex;
}
.img-item{
    margin: 0.3rem;
}
.img-item:nth-child(1),
.img-item:nth-child(2),
.img-item:nth-child(3){
    margin-right: 0;
}
.img-item:hover{
    opacity: 0.8;
}
.name-product{
    text-decoration: none;
    text-transform: uppercase;
    font-weight: 400;
    font-size: 1.9rem;
    display: inline-block;
    margin-bottom: 0.5rem;
    background: #ff4d25;
    color: #fff;
    padding: 0 0.3rem;
    transition: all 0.5s ease;
}
.name-product:hover{
    opacity: 0.9;
}

.product-price{
    margin: 1rem 0;
    font-size: 1rem;
    font-weight: 700;
}
.product-price span{
    font-weight: 400;
}
.last-price span{
    color: #f64749;
    text-decoration: line-through;
}
.new-price span{
    color:  #ff4d25;
}
.product-detail h2{
    text-transform: capitalize;
    color: #12263a;
    padding-bottom: 0.6rem;
}
.product-detail p{
    font-size: 0.9rem;
    padding: 0.3rem;
}
.purchase-info{
    margin: 1.5rem 0;
}
.purchase-info input,
.purchase-info .btn{
    border: 1.5px solid #ddd;
    border-radius: 25px;
    text-align: center;
    padding: 0.45rem 0.8rem;
    outline: 0;
    margin-right: 0.2rem;
    margin-bottom: 1rem;
}
.purchase-info input{
    width: 60px;
}
.purchase-info .btn{
    cursor: pointer;
    color: #fff;
}
.purchase-info .btn:last-of-type{
    background: #333;
}
.purchase-info .btn:hover{
    opacity: 0.9;
}
@media screen and (min-width: 992px){
    .card-detail{
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        grid-gap: 1.5rem;
    }
    .card-wrapper{
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .product-imgs{
        display: flex;
        flex-direction: column;
        justify-content: center;
    }
}
  </style>