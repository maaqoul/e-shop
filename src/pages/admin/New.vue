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
          :class="{ 'form-control': true, error: errors && errors.has('name') }"
        />
        <span class="small text-danger" v-show="errors && errors.has('name')">
          Name is required
        </span>
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
          :class="{ error: errors && errors.has('price') }"
        />
        <span class="small text-danger" v-show="errors && errors.has('price')">
          Price is required
        </span>
      </div>
      <div class="form-group">
        <label>Manufacturer</label>
        <select
          name="manufacturer"
          class="form-control"
          v-model="model.manufacturer"
          v-validate="'required'"
          :class="{ error: errors && errors.has('manufacturer') }"
        >
          <template v-for="manufacturer in manufacturers">
            <option
              :value="manufacturer._id"
              :key="manufacturer._id"
              :selected="
                manufacturer._id ===
                  (model.manufacturer && model.manufacturer._id)
              "
            >
              {{ manufacturer.name }}
            </option>
          </template>
        </select>
        <span
          class="small text-danger"
          v-show="errors && errors.has('manufacturer')"
        >
          Manufacturer is required
        </span>
      </div>
    </div>
    <div class="col-lg-4 col-md-4 col-sm-12 col-xs-12">
      <div class="form-group">
        <label>Image</label>
        <input
          type="text"
          lass="form-control"
          placeholder="Image"
          v-model="model.image"
          v-validate="'required|url'"
          name="image"
          :class="{ 'form-control': true, error: errors && errors.has('image') }"
        />
        <span class="small text-danger" v-show="errors && errors.has('image')"
          >Image is required and must be a valid URL</span
        >
      </div>
      <div class="form-group">
        <label>Description</label>
        <textarea
          type="number"
          class="form-control"
          placeholder="Description"
          rows="5"
          v-model="model.description"
          v-validate="'required'"
          name="description"
          :class="{ 'form-control': true, error: errors && errors.has('description') }"
        ></textarea>
        <span class="small text-danger" v-show=" errors && errors.has('description')"
          >Description is required</span
        >
      </div>
      <div class="form-group new-button">
        <button class="button">
          <i class="fa fa-pencil"></i>
          <span v-if="isEditing">Update Product</span>
          <span v-else>Add Product</span>
        </button>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  name: 'new',
  data() {
    return {
      model: {
        name: 'dummy',
        price: '20',
        manufacturer: 'manufacturer',
        image: '/img.jpg',
        description: 'this is a description',
      },
    };
  },
  methods: {
    saveProduct() {
      // eslint-disable-next-line
      console.log(this.errors);
    },
  },
};
</script>

<style scoped>
.form-control.error {
  border-color: #ff3333;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075),
    0 0 8px rgba(255, 71, 71, 0.6);
}
</style>
