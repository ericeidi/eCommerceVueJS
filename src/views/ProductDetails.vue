<template>
  <div>
  <Alert :alert="alert" />
        <b-container class="m-2">
          <b-row align-v="center">
            <b-col><b-img thumbnail fluid src="https://picsum.photos/250/250/?image=54" alt="Image 1"></b-img></b-col>
            <b-col><h6>Product Name: </h6> <p><small>{{ product.name }}</small></p></b-col>
             <b-col><h6>Product Description: </h6> <p><small>{{ product.description }}</small></p></b-col>
            <b-col><h6>Shipping Cost: </h6> <p><small>{{ product.shippingCost | formatMoney() }}</small></p></b-col>
            <b-col><h6>Unit Price: </h6> <p><small>{{ product.price | formatMoney() }}</small></p></b-col>
          </b-row>
        </b-container>
  </div>
</template>

<script>
import { mapActions } from 'vuex'
import Alert from '@/components/Alert'

export default {
  data () {
    return {
      product: {},
      alert: {
        show: false,
        variant: '',
        message: ''
      }
    }
  },
  created: async function () {
    this.product = await this.getProductById(this.$route.params.id)
  },
  components: {
    Alert
  },
  methods: {
    ...mapActions([
      'getProductById'
    ])
  }
}
</script>
