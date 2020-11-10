<template>
  <main
    class="flex-1 relative z-0 overflow-y-auto focus:outline-none"
    tabindex="0"
  >
    <!-- Page title & actions -->
    <div
      class="border-b border-gray-200 px-4 py-4 sm:flex sm:items-center sm:justify-between sm:px-6 lg:px-8"
    >
      <div class="flex-1 min-w-0">
        <h1 class="text-lg font-medium leading-6 text-gray-900 sm:truncate">
          Create Variant
        </h1>
      </div>
      <div class="mt-4 flex sm:mt-0 sm:ml-4">

          <div class="relative rounded-md shadow-sm">
            <div
              class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none"
            >
              <svg
                class="mr-3 h-4 w-4 text-gray-400"
                viewBox="0 0 20 20"
                fill="currentColor"
              >
                <path
                  fill-rule="evenodd"
                  d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
                  clip-rule="evenodd"
                />
              </svg>
            </div>
            <input
              id="search"
              class="form-input block w-full pl-9 sm:text-sm sm:leading-5"
              placeholder="Search"
            />
          </div>

        <span class="order-0 sm:order-1 sm:ml-3 shadow-sm rounded-md">
          <button
            type="button"
            class="inline-flex items-center px-4 py-2 border border-transparent text-sm leading-5 font-medium rounded-md text-white bg-purple-600 hover:bg-purple-500 focus:outline-none focus:shadow-outline-purple focus:border-purple-700 active:bg-indigo-700 transition duration-150 ease-in-out"
          >
            Create
          </button>
        </span>
      </div>
    </div>
    <div class="bg-white border-b border-gray-200 overflow-hidden">
      <div class="px-4 py-5 sm:px-8">
        <form ref="form" @submit.prevent="createVatiant">
          <div class="mt-6 grid grid-cols-1 gap-y-6 gap-x-4 sm:grid-cols-6">
            <div class="sm:col-span-3">
              <label for="first_name" class="block text-sm font-medium leading-5 text-gray-700">
                Quantity
              </label>
              <div class="mt-1 rounded-md shadow-sm">
                <input v-model.number="variant.quantity" id="first_name" class="form-input block w-full transition duration-150 ease-in-out sm:text-sm sm:leading-5">
              </div>
            </div>

            <div class="sm:col-span-3">
              <label for="last_name" class="block text-sm font-medium leading-5 text-gray-700">
                Price
              </label>
              <div class="mt-1 rounded-md shadow-sm">
                <input v-model.number="variant.price" id="last_name" class="form-input block w-full transition duration-150 ease-in-out sm:text-sm sm:leading-5">
              </div>
            </div>

            <div class="sm:col-span-3">
              <label for="last_name" class="block text-sm font-medium leading-5 text-gray-700">
                Size
              </label>
              <div class="mt-1 rounded-md shadow-sm">
                <input v-model="variant.size" id="last_name" class="form-input block w-full transition duration-150 ease-in-out sm:text-sm sm:leading-5">
              </div>
            </div>

            <div class="sm:col-span-3">
              <label for="last_name" class="block text-sm font-medium leading-5 text-gray-700">
                Color
              </label>
              <div class="mt-1 rounded-md shadow-sm">
                <input v-model="variant.color" id="last_name" class="form-input block w-full transition duration-150 ease-in-out sm:text-sm sm:leading-5">
              </div>
            </div>
          </div>
          <div class="mt-8 pt-5">
            <div class="flex justify-end">
              <span class="inline-flex rounded-md shadow-sm">
                <button type="button" class="py-2 px-4 border border-gray-300 rounded-md text-sm leading-5 font-medium text-gray-700 hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:bg-gray-50 active:text-gray-800 transition duration-150 ease-in-out">
                  Cancel
                </button>
              </span>
              <span class="ml-3 inline-flex rounded-md shadow-sm">
                <button type="submit" class="inline-flex justify-center py-2 px-4 border border-transparent text-sm leading-5 font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-500 focus:outline-none focus:border-indigo-700 focus:shadow-outline-indigo active:bg-indigo-700 transition duration-150 ease-in-out">
                  Create
                </button>
              </span>
            </div>
          </div>
        </form>
      </div>
    </div>
  </main>
</template>

<script>
import gql from "graphql-tag";

export default {
  middleware: ["authenticated"],
  layout: "navigation",
  data() {
    return {
      variant: {},
      errors: [],
    };
  },
  methods: {
    createVatiant() {
      this.$apollo
        .mutate({
          mutation: gql`
            mutation createVariant($quantity: Int!, $price: Float!, $size: String!, $color: String!, $productId: ID!) {
              createVariant(input: { quantity: $quantity, price: $price, size: $size, color: $color, productId: $productId }) {
                variant {
                  id
                  sku
                  quantity
                  price
                }
              }
            }
          `,
          variables: {
            quantity: this.variant.quantity,
            price: this.variant.price,
            size: this.variant.size,
            color: this.variant.color,
            productId: Number(this.$route.params.id)
          },
        })
        .then((data) => {
          this.$router.push("/products");
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
};
</script>
