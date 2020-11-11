<template>
  <div class="fixed inset-0 overflow-hidden">
    <div class="absolute inset-0 bg-gray-500 bg-opacity-75 transition-opacity">
      <section class="absolute inset-y-0 right-0 pl-10 max-w-full flex sm:pl-16">
        <!--
          Slide-over panel, show/hide based on slide-over state.

          Entering: "transform transition ease-in-out duration-500 sm:duration-700"
            From: "translate-x-full"
            To: "translate-x-0"
          Leaving: "transform transition ease-in-out duration-500 sm:duration-700"
            From: "translate-x-0"
            To: "translate-x-full"
        -->
        <form ref="form" class="w-screen max-w-2xl" @submit.prevent="createProduct" v-click-outside="externalClick">
          <div class="h-full flex flex-col bg-white shadow-xl overflow-y-scroll">
            <div class="flex-1">
              <!-- Header -->
              <header class="px-4 py-6 bg-gray-50 sm:px-6">
                <div class="flex items-start justify-between space-x-3">
                  <div class="space-y-1">
                    <h2 class="text-lg leading-7 font-medium text-gray-900">
                      New project
                    </h2>
                    <p class="text-sm text-gray-500 leading-5">
                      Get started by filling in the information below to create your new project.
                    </p>
                  </div>
                  <div class="h-7 flex items-center">
                    <button
                      aria-label="Close panel"
                      class="text-gray-400 hover:text-gray-500 transition ease-in-out duration-150"
                      @click="changeStatus()"
                    >
                      <!-- Heroicon name: x -->
                      <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                      </svg>
                    </button>
                  </div>
                </div>
              </header>

              <!-- Divider container -->
              <div class="py-6 space-y-6 sm:py-0 sm:space-y-0 sm:divide-y sm:divide-gray-200">
                <!-- Product name -->
                <div class="space-y-1 px-4 sm:space-y-0 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6 sm:py-5">
                  <div>
                    <label for="product_name" class="block text-sm font-medium leading-5 text-gray-900 sm:mt-px sm:pt-2">
                      Name
                    </label>
                  </div>
                  <div class="sm:col-span-2">
                    <div class="rounded-md shadow-sm">
                      <input v-model="product.name" id="product_name" class="form-input block w-full sm:text-sm sm:leading-5" placeholder="">
                    </div>
                  </div>
                </div>

                <!-- Product description -->
                <div class="space-y-1 px-4 sm:space-y-0 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6 sm:py-5">
                  <div>
                    <label for="product_description" class="block text-sm font-medium leading-5 text-gray-900 sm:mt-px sm:pt-2">
                      Description
                    </label>
                  </div>
                  <div class="sm:col-span-2">
                    <div class="flex rounded-md shadow-sm">
                      <textarea v-model="product.description" id="product_description" class="form-input block w-full sm:text-sm sm:leading-5" placeholder="" />
                    </div>
                  </div>
                </div>

                <!-- Product brand -->
                <div class="space-y-1 px-4 sm:space-y-0 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6 sm:py-5">
                  <div>
                    <label for="product_brand" class="block text-sm font-medium leading-5 text-gray-900 sm:mt-px sm:pt-2">
                      Brand
                    </label>
                  </div>
                  <div class="sm:col-span-2">
                    <div class="flex rounded-md shadow-sm">
                      <select v-model.number="product.brandId" id="location" class="mt-1 form-select block w-full pl-3 pr-10 py-2 text-base leading-6 border-gray-300 focus:outline-none focus:shadow-outline-blue focus:border-blue-300 sm:text-sm sm:leading-5">
                        <option v-for="brand in allBrands" :key="brand.id" :value="brand.id" >{{ brand.name }}</option>
                      </select>
                    </div>
                  </div>
                </div>

                <!-- Product tag -->
                <div class="space-y-1 px-4 sm:space-y-0 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6 sm:py-5">
                  <div>
                    <label for="product_tag" class="block text-sm font-medium leading-5 text-gray-900 sm:mt-px sm:pt-2">
                      Category
                    </label>
                  </div>
                  <div class="sm:col-span-2">
                    <div class="flex rounded-md shadow-sm">
                      <select v-model.number="product.tagId" id="country" class="mt-1 form-select block w-full pl-3 pr-10 py-2 text-base leading-6 border-gray-300 focus:outline-none focus:shadow-outline-blue focus:border-blue-300 sm:text-sm sm:leading-5">
                        <option v-for="tag in allTags" :key="tag.id" :value="tag.id" >{{ tag.name }}</option>
                      </select>
                    </div>
                  </div>
                </div>

                <!-- Product package -->
                <div class="space-y-1 px-4 sm:space-y-0 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6 sm:py-5">
                  <div>
                    <label for="product_package" class="block text-sm font-medium leading-5 text-gray-900 sm:mt-px sm:pt-2">
                      Package
                    </label>
                  </div>
                  <div class="sm:col-span-2">
                    <div class="flex rounded-md shadow-sm">
                      <select v-model.number="product.packageId" id="location" class="mt-1 form-select block w-full pl-3 pr-10 py-2 text-base leading-6 border-gray-300 focus:outline-none focus:shadow-outline-blue focus:border-blue-300 sm:text-sm sm:leading-5">
                        <option v-for="pack in allPackages" :key="pack.id" :value="pack.id" >{{ pack.name }}</option>
                      </select>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <!-- Action buttons -->
            <div class="flex-shrink-0 px-4 border-t border-gray-200 py-5 sm:px-6">
              <div class="space-x-3 flex justify-end">
                <span class="inline-flex rounded-md shadow-sm">
                  <button
                    type="button"
                    class="py-2 px-4 border border-gray-300 rounded-md text-sm leading-5 font-medium text-gray-700 hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:bg-gray-50 active:text-gray-800 transition duration-150 ease-in-out"
                    @click="changeStatus()"
                  >
                    Cancel
                  </button>
                </span>
                <span class="inline-flex rounded-md shadow-sm">
                  <button type="submit" class="inline-flex justify-center py-2 px-4 border border-transparent text-sm leading-5 font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-500 focus:outline-none focus:border-indigo-700 focus:shadow-outline-indigo active:bg-indigo-700 transition duration-150 ease-in-out">
                    Create
                  </button>
                </span>
              </div>
            </div>
          </div>
        </form>
      </section>
    </div>
  </div>
</template>

<script>
import gql from "graphql-tag";
import vClickOutside from 'v-click-outside';

export default {
  data() {
    return {
      product: {},
      allBrands: [],
      allTags: [],
      allPackages: [],
      errors: [],
    }
  },
  directives: {
    clickOutside: vClickOutside.directive
  },
  methods: {
    externalClick (event) {
      this.$emit('changeStatus')
    },
    changeStatus() {
      this.$emit('changeStatus')
    },
    createProduct() {
      this.$apollo
        .mutate({
          mutation: gql`
            mutation createProduct($name: String!, $description: String!, $brandId: ID!, $tagId: ID!, $packageId: ID!) {
              createProduct(input: { name: $name, description: $description, brandId: $brandId, tagId: $tagId, packageId: $packageId }) {
                product {
                  id
                  name
                  description
                  stripeProduct
                }
              }
            }
          `,
          variables: {
            name: this.product.name,
            description: this.product.description,
            brandId: this.product.brandId,
            tagId: this.product.tagId,
            packageId: this.product.packageId,
          },
        })
        .then((data) => {
          if (data) {
            location.reload()
          }
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
  apollo: {
    allBrands: {
      query: gql`
        query {
          allBrands {
            id
            name
          }
        }
      `
    },
    allTags: {
      query: gql`
        query {
          allTags {
            id
            name
          }
        }
      `
    },
    allPackages: {
      query: gql`
        query {
          allPackages {
            id
            name
          }
        }
      `
    }
  }
}
</script>
