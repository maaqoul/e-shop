<template>
  <form @submit.prevent="saveProduct">
      <div class="col-lg-5 col-md-5 col-sm-12 col-xs-12">
          <div class="form-group">
              <label>Name</label>
              <input
               type="text"
               name="name"
               placeholder="Name"
               v-model="model.name"
               v-validate="'required'"
               :class="{'form-control': true, 'error': errors.has('name')}">
               <span class="small text-danger" v-show="errors.has('name')">Name is required</span>
          </div>
          <div class="form-group">
              <label>Price</label>
              <input
               type="number"
               name="price"
               class="form-control"
               placeholder="Price"
               v-model="model.price"
               v-validate="'required'"
               :class="{'error': errors.has('price') }" >
               <span class="small text-danger" v-show="errors.has('price')">Price is required</span>
          </div>
          <div class="form-group">
              <label>Manufacturer</label>
              <select
               name="manufacturer"
               class="form-control"
               v-model="model.manufacturer"
               v-validate="'required'"
               :class="{'error': errors.has('manufacturer')}"
               ></select>
          </div>
      </div>
  </form>
</template>

<script>
export default {
  name: 'new',
  methods: {
    saveProduct() {
    // eslint-disable-next-line
      console.log(this.erros);
    },
  },
};
</script>

<style  scoped>

.form-control.error {
  border-color: #FF3333;
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(255, 71, 71, 0.6);
}

</style>
