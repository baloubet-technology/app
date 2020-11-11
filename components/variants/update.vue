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
        <form ref="form" class="w-screen max-w-2xl" @submit.prevent="updateVariant" v-click-outside="externalClick">
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
                <!-- Variant quantity -->
                <div class="space-y-1 px-4 sm:space-y-0 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6 sm:py-5">
                  <div>
                    <label for="variant_quantity" class="block text-sm font-medium leading-5 text-gray-900 sm:mt-px sm:pt-2">
                      Quantity
                    </label>
                  </div>
                  <div class="sm:col-span-2">
                    <div class="rounded-md shadow-sm">
                      <input v-model.number="variantId.quantity" id="variant_quantity" class="form-input block w-full sm:text-sm sm:leading-5" placeholder="">
                    </div>
                  </div>
                </div>

                <!-- Variant price -->
                <div class="space-y-1 px-4 sm:space-y-0 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6 sm:py-5">
                  <div>
                    <label for="variant_price" class="block text-sm font-medium leading-5 text-gray-900 sm:mt-px sm:pt-2">
                      Price
                    </label>
                  </div>
                  <div class="sm:col-span-2">
                    <div class="flex rounded-md shadow-sm">
                      <input v-model.number="variantId.price" id="variant_price" class="form-input block w-full sm:text-sm sm:leading-5" placeholder="">
                    </div>
                  </div>
                </div>

                <!-- Variant size -->
                <div class="space-y-1 px-4 sm:space-y-0 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6 sm:py-5">
                  <div>
                    <label for="variant_size" class="block text-sm font-medium leading-5 text-gray-900 sm:mt-px sm:pt-2">
                      Size
                    </label>
                  </div>
                  <div class="sm:col-span-2">
                    <div class="flex rounded-md shadow-sm">
                      <input v-model="variantId.size" id="variant_size" class="form-input block w-full sm:text-sm sm:leading-5" placeholder="">
                    </div>
                  </div>
                </div>

                <!-- Variant color -->
                <div class="space-y-1 px-4 sm:space-y-0 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-6 sm:py-5">
                  <div>
                    <label for="variant_color" class="block text-sm font-medium leading-5 text-gray-900 sm:mt-px sm:pt-2">
                      Color
                    </label>
                  </div>
                  <div class="sm:col-span-2">
                    <div class="flex rounded-md shadow-sm">
                      <input v-model="variantId.color" id="variant_color" class="form-input block w-full sm:text-sm sm:leading-5" placeholder="">
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
                    Update
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
  props: ['id'],
  data() {
    return {
      variantId: {},
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
    updateVariant() {
      this.$apollo
        .mutate({
          mutation: gql`
            mutation updateVariant($quantity: Int!, $price: Float!, $size: String!, $color: String!, $id: ID!) {
              updateVariant(input: { quantity: $quantity, price: $price, size: $size, color: $color, id: $id }) {
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
            quantity: this.variantId.quantity,
            price: this.variantId.price,
            size: this.variantId.size,
            color: this.variantId.color,
            id: Number(this.$props.id)
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
    variantId: {
      query: gql`
        query($id: ID!) {
          variantId(id: $id) {
            id
            quantity
            price
            size
            color
          }
        }
      `,
      variables() {
        return { id: this.$props.id }
      },
    }
  }
}
</script>
