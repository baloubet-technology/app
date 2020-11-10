<template>
  <main
    class="flex-1 relative z-0 overflow-y-auto focus:outline-none"
    tabindex="0"
  >
    <!-- Page title & actions -->

    <div
      class="border-b border-gray-200 px-4 py-4 sm:flex sm:items-center sm:justify-between sm:px-6 lg:px-8"
    >
      <div>
        <div class="sm:hidden">
          <select aria-label="Selected tab" class="form-select block w-full">
            <option>My Account</option>
            <option>Company</option>
            <option selected>Team Members</option>
            <option>Billing</option>
          </select>
        </div>
        <div class="hidden sm:block">
          <nav class="flex">
            <nuxt-link :to="{ name: 'products-id', params: { id: this.$route.params.id }}" class="px-3 py-2 font-medium text-sm leading-5 rounded-md text-gray-600 hover:text-gray-800 focus:outline-none focus:text-gray-800 focus:bg-gray-200">
              Infos
            </nuxt-link>
            <a href="#" class="ml-4 px-3 py-2 font-medium text-sm leading-5 rounded-md text-gray-800 bg-gray-200 focus:outline-none focus:bg-gray-300" aria-current="page">
              Variants
            </a>
          </nav>
        </div>
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
          <nuxt-link
            :to="{ name: 'products-id-variants-create', params: { id: this.$route.params.id }}"
          >
            <button
              type="button"
              class="inline-flex items-center px-4 py-2 border border-transparent text-sm leading-5 font-medium rounded-md text-white bg-purple-600 hover:bg-purple-500 focus:outline-none focus:shadow-outline-purple focus:border-purple-700 active:bg-indigo-700 transition duration-150 ease-in-out"
            >
              Create
            </button>
          </nuxt-link>
        </span>
      </div>
    </div>
    <!-- Projects table (small breakpoint and up) -->
    <div class="hidden sm:block">
      <div
        class="align-middle inline-block min-w-full border-b border-gray-200"
      >
        <table class="min-w-full">
          <thead>
            <tr class="border-gray-200">
              <th
                class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
              >
                <span class="lg:pl-2">Sku</span>
              </th>
              <th
                class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
              >
                Size
              </th>
              <th
                class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
              >
                Color
              </th>
              <th
               class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
              >
                Quantity
              </th>
              <th
                class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
              >
                Price
              </th>
              <th
                class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
              ></th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-100">
            <tr v-for="variant in productId.variant">
              <td
                class="px-6 py-3 max-w-0 w-full whitespace-no-wrap text-sm leading-5 font-medium text-gray-900"
              >
                <div class="flex items-center space-x-3 lg:pl-2">
                  <div
                    class="flex-shrink-0 w-2.5 h-2.5 rounded-full bg-pink-600"
                  ></div>
                  <a href="#" class="truncate hover:text-gray-600">
                    <span>
                      {{ variant.sku }}
                    </span>
                  </a>
                </div>
              </td>
              <td
                class="hidden md:table-cell px-6 py-3 whitespace-no-wrap text-sm leading-5 text-gray-500 text-right"
              >
                {{ variant.size }}
              </td>
              <td
                class="hidden md:table-cell px-6 py-3 whitespace-no-wrap text-sm leading-5 text-gray-500 text-right"
              >
                {{ variant.color }}
              </td>
              <td
                class="hidden md:table-cell px-6 py-3 whitespace-no-wrap text-sm leading-5 text-gray-500 text-right"
              >
                {{ variant.quantity }}
              </td>
              <td
                class="hidden md:table-cell px-6 py-3 whitespace-no-wrap text-sm leading-5 text-gray-500 text-right"
              >
                {{ variant.price }}
              </td>
              <td class="pr-6">
                <div class="relative flex justify-end items-center">
                  <button
                    id="project-options-menu-0"
                    aria-has-popup="true"
                    type="button"
                    class="w-8 h-8 inline-flex items-center justify-center text-gray-400 rounded-full bg-transparent hover:text-gray-500 focus:outline-none focus:text-gray-500 focus:bg-gray-100 transition ease-in-out duration-150"
                  >
                    <svg
                      class="w-5 h-5"
                      viewBox="0 0 20 20"
                      fill="currentColor"
                    >
                      <path
                        d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z"
                      />
                    </svg>
                  </button>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
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
      id: null,
      productId: null,
      errors: [],
    };
  },
  apollo: {
    productId: {
      query: gql`
        query($id: ID!) {
          productId(id: $id) {
            id
            name
            variant {
              id
              sku
              size
              color
              price
              quantity
            }
          }
        }
      `,
      variables() {
        return { id: this.$route.params.id }
      },
    }
  }
};
</script>
