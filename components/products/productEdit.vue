<template>
  <div class="fixed inset-0 overflow-hidden">
    <div class="absolute inset-0 bg-gray-500 bg-opacity-75 transition-opacity">
      <section class="absolute inset-y-0 pl-16 max-w-full right-0 flex">
        <div class="w-screen max-w-md">
          <div class="h-full divide-y divide-gray-200 flex flex-col bg-white shadow-xl">
            <div class="flex-1 h-0 overflow-y-auto">
              <header class="space-y-1 py-6 px-4 bg-indigo-700 sm:px-6">
                <div class="flex items-center justify-between space-x-3">
                  <h2 class="text-lg leading-7 font-medium text-white">
                    Update this user
                  </h2>
                  <div class="h-7 flex items-center">
                    <button
                      aria-label="Close panel"
                      class="text-indigo-200 hover:text-white transition ease-in-out duration-150"
                      @click="changeStatus()"
                    >
                      <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path
                          stroke-linecap="round"
                          stroke-linejoin="round"
                          stroke-width="2"
                          d="M6 18L18 6M6 6l12 12"
                        />
                      </svg>
                    </button>
                  </div>
                </div>
                <div>
                  <p class="text-sm leading-5 text-indigo-300">
                    The gray fields are not editable. Always edit carefully, no going back is possible. Use in
                    moderation. 😉
                  </p>
                </div>
              </header>
              <div class="flex-1 flex flex-col justify-between">
                <div class="px-4 divide-y divide-gray-200 sm:px-6">
                  <div class="space-y-6 pt-6 pb-5">
                    <div class="space-y-1">
                      <label for="project_name" class="block text-sm font-medium leading-5 text-gray-900">
                        Id
                      </label>
                      <div class="relative rounded-md shadow-sm">
                        {{ orderOrganization.id }}
                      </div>
                    </div>
                    <div class="space-y-1">
                      <label for="project_name" class="block text-sm font-medium leading-5 text-gray-900">
                        Email
                      </label>
                      <div class="relative rounded-md shadow-sm">
                        {{ orderOrganization.price }}
                      </div>
                    </div>
                    <cld-image
                      :public-id="orderOrganization.sku"
                    />
                  </div>
                </div>
              </div>
            </div>
            <div class="flex-shrink-0 px-4 py-4 space-x-4 flex justify-end">
              <span class="inline-flex rounded-md shadow-sm">
                <button
                  @click="changeStatus()"
                  type="button"
                  class="py-2 px-4 border border-gray-300 rounded-md text-sm leading-5 font-medium text-gray-700 hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:bg-gray-50 active:text-gray-800 transition duration-150 ease-in-out"
                >
                  Cancel
                </button>
              </span>
              <span class="inline-flex rounded-md shadow-sm">
                <button
                  :href="orderOrganization.orderUrl"
                  target="_blank"
                  type="button"
                  class="inline-flex justify-center w-full rounded-md border border-transparent px-4 py-2 bg-red-600 text-base leading-6 font-medium text-white shadow-sm hover:bg-red-500 focus:outline-none focus:border-red-700 focus:shadow-outline-red transition ease-in-out duration-150 sm:text-sm sm:leading-5"
                >
                  Invoice
                </button>
              </span>
              <span class="inline-flex rounded-md shadow-sm">
                <button
                  :href="orderOrganization.shippingLabel"
                  target="_blank"
                  type="button"
                  class="inline-flex justify-center py-2 px-4 border border-transparent text-sm leading-5 font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-500 focus:outline-none focus:border-indigo-700 focus:shadow-outline-indigo active:bg-indigo-700 transition duration-150 ease-in-out"
                >
                  Label
                </button>
              </span>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import gql from "graphql-tag";

export default {
  props: ['id'],
  data() {
    return {
      orderOrganization: null,
      errors: [],
    }
  },
  methods: {
    changeStatus() {
      this.$emit('changeStatus')
    },
  },
  apollo: {
    orderOrganization: {
      query: gql`
        query($id: ID!) {
          orderOrganization(id: $id) {
            id
            price
            shippingLabel
            status
            orderUrl
            variant {
              id
              pictureUrl
              product {
                name
              }
            }
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
