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
          Products
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
            @click="createProductPopup = !createProductPopup;"
            class="inline-flex items-center px-4 py-2 border border-transparent text-sm leading-5 font-medium rounded-md text-white bg-purple-600 hover:bg-purple-500 focus:outline-none focus:shadow-outline-purple focus:border-purple-700 active:bg-indigo-700 transition duration-150 ease-in-out"
          >
            Create
          </button>
        </span>
      </div>
    </div>

    <!-- Projects list (only on smallest breakpoint) -->
    <div class="pt-2 pb-6 md:py-6">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 md:px-8">
        <ul class="grid grid-cols-1 gap-6 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4">

          <li v-for="product in allProducts" class="col-span-1 flex flex-col text-center bg-white rounded-lg shadow">
            <img class="p-6" src="https://res.cloudinary.com/baloubet/image/upload/v1594141696/sku_HbXLvkzmGIBCH5.png" alt="">
            <div class="border-t border-gray-200">
              <div class="-mt-px flex">
                <div class="w-0 flex-1 flex">
                  <nuxt-link :to="{ name: 'products-id', params: { id: product.id }}" class="relative -mr-px w-0 flex-1 inline-flex items-center justify-center py-4 text-sm leading-5 text-gray-700 font-medium border border-transparent rounded-bl-lg rounded-br-lg hover:text-gray-500 focus:outline-none focus:shadow-outline-blue focus:border-blue-300 focus:z-10 transition ease-in-out duration-150">
                    <div>
                      <p class="text-sm leading-5 font-medium text-gray-500">{{ product.brand.name }}</p>
                      <p class="mt-1 text-sm leading-5 text-gray-900">{{ product.name }}</p>
                      <p class="mt-4 text-gray-900">1590$</p>
                    </div>
                  </nuxt-link>
                </div>
              </div>
            </div>
          </li>

        </ul>
      </div>
    </div>
    <div
      v-if="createProductPopup"
    >
      <CreateProduct
        @changeStatus="createProductPopup = false"
      />
    </div>
  </main>
</template>

<script>
import gql from "graphql-tag";
import CreateProduct from '@/components/products/create';

export default {
  middleware: ["authenticated"],
  layout: "navigation",
  components: {
    CreateProduct,
  },
  data() {
    return {
      id: null,
      allProducts: null,
      createProductPopup: false,
      errors: [],
    };
  },
  apollo: {
    allProducts: {
      query: gql`
        query {
          allProducts {
            id
            name
            description
            brand {
              name
            }
          }
        }
      `
    }
  }
};
</script>
