<template>
  <BasicLayouts>
    <br>
    <h1>Encuentra aquí el producto que necesitas para el cuidado y recuperación de tu salud</h1>
    <br>
    <br>
    <br>
    <div class="ui grid">
      <div
        class="sixten wide mobile eight wide tablet four wide computer column"
        v-for="product in products"
        :key="product.id"
      >
        <Product :product="product" />
      </div>
    </div>
        <!-- Inicio de Sección la ubicacion y contacto de la pagia web  -->
    <div class="ui inverted segment">
      <div class="ui segment">
        <div class="ui two column very relaxed grid">
          <div class="column">
            <h1>Pharmaweb</h1>
            <p>Dirección : Avenida Rua duarte pacheco</p>
          </div>
          <div class="column">
            <div class="ui small image">
              <body>
                <a
                  href="https://www.google.com/maps/place/Pharmacy+Central+de+Odivelas/@38.788385,-9.1768487,3a,78.7y,243.26h,92.57t/data=!3m7!1e1!3m5!1s_QbLo_wWU3JZ3DWb2q0EHQ!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fpanoid%3D_QbLo_wWU3JZ3DWb2q0EHQ%26cb_client%3Dsearch.gws-prod.gps%26w%3D86%26h%3D86%26yaw%3D244.1348%26pitch%3D0%26thumbfov%3D100!7i16384!8i8192!4m9!1m2!2m1!1spharmacies!3m5!1s0xd1932a676581c21:0x3be322a5cfbb5f55!8m2!3d38.7883544!4d-9.1769579!15sCgpwaGFybWFjaWVzWgwiCnBoYXJtYWNpZXOSAQhwaGFybWFjeQ"
                >
                  <img
                    src="https://www.zyrgon.com/wp-content/uploads/2019/06/googlemaps-Zyrgon.jpg"
                    width="450"
                    height="90"
                  />
                </a>
              </body>
            </div>
          </div>
        </div>
        <div class="ui vertical divider">
          <i class="arrow alternate circle right outline icon"></i>
        </div>
      </div>
      <p></p>
      <div class="ui inverted divider"></div>
      <div class="ui segment">
        <div class="ui two column very relaxed grid">
          <div class="column">
            <h1>Contactanos</h1>
            <p>PHONE NUMBER: 217 946 400</p>
            <p>EMAIL: pharmawebmintic@gmail.com</p>
          </div>
          <div class="column">
            <div >
              <i class="huge green whatsapp square icon"></i>
            </div>
            <div>
              <i class="huge pink instagram icon" ></i>
            </div>
          </div>
        </div>
        <div class="ui vertical divider">
          <i class="arrow alternate circle right outline icon"></i>
        </div>
      </div>
      <h4 class="ui horizontal inverted divider">
        “Hacer o no hacer. No sirve intentar, solo hacer”
      </h4>
    </div>
  <!-- Final de la sección de ubicación y contacto  -->
  </BasicLayouts>
</template>

<script>
import { ref, onMounted } from 'vue';
import BasicLayouts from '../layouts/BasicLayouts.vue';
import { getProducts } from '../api/products';
import Product from '../components/Product.vue';
export default {
  name: 'Home',
  components: {
    BasicLayouts,
    Product,
  },

  setup() {
    let products = ref(null);

    onMounted(async () => {
      const response = await getProducts(20);
      products.value = response;
    });
    return {
      products,
    };
  },
};
</script>
