<template>
  <q-layout view="hHh lpR fFf">
    <!-- Navbar -->
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title class="q-ml-md">
          <q-avatar size="42px">
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg" />
          </q-avatar>
          <span class="q-ml-sm text-h6">Toko Sneakers Kikss</span>
        </q-toolbar-title>
      </q-toolbar>
      <q-tabs align="left">
        <q-route-tab to="/home" label="Beranda" />
        <q-route-tab to="/top-seller" label="Top Seller" />
        <q-route-tab
          to="/about"
          label="Tentang Kami"
          @click.prevent="openDrawer"
        />
      </q-tabs>
    </q-header>

    <!-- Drawer -->
    <q-drawer v-model="leftDrawerOpen" side="left" bordered>
      <q-scroll-area class="fit">
        <q-list padding class="menu-list">
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="inbox" />
            </q-item-section>
            <q-item-section class="text-black"> Inbox </q-item-section>
          </q-item>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="star" />
            </q-item-section>
            <q-item-section class="text-black"> Star </q-item-section>
          </q-item>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="send" />
            </q-item-section>
            <q-item-section class="text-black"> Send </q-item-section>
          </q-item>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="drafts" />
            </q-item-section>
            <q-item-section class="text-black"> Drafts </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
    </q-drawer>

    <!-- Page Container -->
    <q-page-container>
      <q-page class="q-pa-md">
        <!-- Carousel -->
        <q-carousel
          v-model="slide"
          animated
          infinite
          control-color="white"
          arrows
          navigation
          navigation-position="bottom"
          swipeable
        >
          <q-carousel-slide
            name="1"
            img-src="https://i.pinimg.com/736x/b5/a8/ca/b5a8cab08bcfa25261a58f9cfb8424e8.jpg"
          >
            <div
              class="absolute-bottom bg-black bg-opacity-50 text-h5 text-white q-pa-sm"
            >
              Promo Terbaik!
            </div>
          </q-carousel-slide>
          <q-carousel-slide
            name="2"
            img-src="https://i.pinimg.com/736x/28/64/09/2864091c5f37d33f96f5a8f9557079be.jpg"
          >
            <div
              class="absolute-bottom bg-black bg-opacity-50 text-h5 text-white q-pa-sm"
            >
              Diskon Spesial!
            </div>
          </q-carousel-slide>
          <q-carousel-slide
            name="3"
            img-src="https://i.pinimg.com/736x/7a/32/d4/7a32d4947edb504a92791a519e18853b.jpg"
          >
            <div
              class="absolute-bottom bg-black bg-opacity-50 text-h5 text-white q-pa-sm"
            >
              Produk Terbaru!
            </div>
          </q-carousel-slide>
        </q-carousel>

        <!-- Card Section -->
        <div class="row q-col-gutter-md q-pt-md">
          <q-card
            v-for="(product, index) in products"
            :key="index"
            class="col-xs-12 col-sm-6 col-md-4 q-hover-shadow"
          >
            <q-img :src="product.image" class="q-mb-sm" :size="product.size" />
            <q-card-section>
              <div class="text-subtitle1 text-black">{{ product.name }}</div>
              <div class="text-caption text-black">
                {{ product.description }}
              </div>
            </q-card-section>
            <q-card-actions align="right">
              <q-btn flat label="Detail" color="primary" />
              <q-btn flat label="Add to Cart" color="primary" />
              <q-btn
                flat
                label="Delete"
                color="negative"
                @click="deleteProduct(index)"
              />
            </q-card-actions>
          </q-card>
        </div>
      </q-page>
    </q-page-container>

    <!-- Footer -->
    <q-footer class="bg-primary-8 text-white q-pa-md">
      <div class="row items-center">
        <div class="col text-black">© 2024 Toko Sneakers Kikss</div>
        <div class="col-auto">
          <q-btn
            flat
            round
            icon="fab fa-facebook"
            class="text-primary q-mr-sm"
          />
          <q-btn
            flat
            round
            icon="fab fa-twitter"
            class="text-primary q-mr-sm"
          />
          <q-btn flat round icon="fab fa-instagram" class="text-primary" />
        </div>
      </div>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const leftDrawerOpen = ref(false);
    const slide = ref("1");
    const products = ref([
      {
        name: "Sneakers 1 kikss",
        description: "Description for product 1",
        image: "https://images.journeys.com/images/products/1_813863_ZM.JPG",
        size: "50px", // Atur ukuran gambar di sini
      },
      {
        name: "Sneakers 2 kikss",
        description: "Description for product 2",
        image: "https://images.journeys.com/images/products/1_729184_ZM.JPG",
        size: "50px", // Atur ukuran gambar di sini
      },
      {
        name: "Sneakers 3 kikss",
        description: "Description for product 3",
        image: "https://images.journeys.com/images/products/1_785521_ZM.jpg",
        size: "50px", // Atur ukuran gambar di sini
      },
      {
        name: "Sneakers 4 kikss",
        description: "Description for product 4",
        image: "https://images.journeys.com/images/products/1_5122_ZM.JPG",
        size: "50px", // Atur ukuran gambar di sini
      },
      {
        name: "Sneakers 5 kikss",
        description: "Description for product 5",
        image: "https://images.journeys.com/images/products/1_5150_ZM.JPG",
        size: "50px", // Atur ukuran gambar di sini
      },
      {
        name: "Sneakers 6 kikss",
        description: "Description for product 6",
        image: "https://images.journeys.com/images/products/1_752142_ZM.JPG",
        size: "50px", // Atur ukuran gambar di sini
      },
      {
        name: "Sneakers 7 kikss",
        description: "Description for product 7",
        image: "https://images.journeys.com/images/products/1_259094_ZM.JPG",
        size: "50px", // Atur ukuran gambar di sini
      },
      {
        name: "Sneakers 8 kikss",
        description: "Description for product 8",
        image: "https://images.journeys.com/images/products/1_810216_ZM.jpg",
        size: "50px", // Atur ukuran gambar di sini
      },
      {
        name: "Sneakers 9 kikss",
        description: "Description for product 9",
        image: "https://images.journeys.com/images/products/1_441156_ZM.JPG",
        size: "50px", // Atur ukuran gambar di sini
      },
    ]);

    function toggleLeftDrawer() {
      leftDrawerOpen.value = !leftDrawerOpen.value;
    }

    function deleteProduct(index) {
      products.value.splice(index, 1);
    }

    function openDrawer() {
      leftDrawerOpen.value = true;
    }

    return {
      leftDrawerOpen,
      slide,
      products,
      toggleLeftDrawer,
      deleteProduct,
      openDrawer,
    };
  },
};
</script>

<style>
.menu-list {
  padding-top: 20px;
}

.q-hover-shadow:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.q-carousel-slide .absolute-bottom {
  background: rgba(0, 0, 0, 0.5);
  padding: 1rem;
  text-align: center;
  width: 100%;
}

.text-black {
  color: black;
}
</style>
