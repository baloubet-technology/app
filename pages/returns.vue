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
          Returns
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
      </div>
    </div>

    <!-- Projects list (only on smallest breakpoint) -->
    <div class="mt-10 sm:hidden">
      <div class="px-4 sm:px-6">
        <h2 class="text-gray-500 text-xs font-medium uppercase tracking-wide">
          Returns
        </h2>
      </div>
      <ul class="mt-3 border-t border-gray-200 divide-y divide-gray-100">
        <li v-for="refund in allRefunds">
          <a
            @click="idRefund(refund.id);"
            class="flex items-center justify-between px-4 py-4 hover:bg-gray-50 sm:px-6"
          >
            <div v-if="refund.status === 'Livré'" class="flex items-center truncate space-x-3">
              <div
                class="w-2.5 h-2.5 flex-shrink-0 rounded-full bg-green-600"
              ></div>
              <p class="font-medium truncate text-sm leading-6">
                {{ refund.status }}
              </p>
            </div>
            <div v-else-if="refund.status === 'En attente'" class="flex items-center truncate space-x-3">
              <div
                class="w-2.5 h-2.5 flex-shrink-0 rounded-full bg-red-600"
              ></div>
              <p class="font-medium truncate text-sm leading-6">
                {{ refund.status }}
              </p>
            </div>
            <div v-else="refund.status" class="flex items-center truncate space-x-3">
              <div
                class="w-2.5 h-2.5 flex-shrink-0 rounded-full bg-yellow-600"
              ></div>
              <p class="font-medium truncate text-sm leading-6">
                {{ refund.status }}
              </p>
            </div>
            <svg
              class="ml-4 h-5 w-5 text-gray-400 group-hover:text-gray-500 group-focus:text-gray-600 transition ease-in-out duration-150"
              viewBox="0 0 20 20"
              fill="currentColor"
            >
              <path
                fill-rule="evenodd"
                d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z"
                clip-rule="evenodd"
              />
            </svg>
          </a>
        </li>

        <!-- More project rows... -->
      </ul>
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
                <span class="lg:pl-2">Status</span>
              </th>
              <th
                class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
              >
                Product
              </th>
              <th
                class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
              >
                Create
              </th>
              <th
                class="pr-6 py-3 border-b border-gray-200 bg-gray-50 text-right text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
              ></th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-100">
            <tr v-for="refund in allRefunds">
              <td
                class="px-6 py-3 max-w-0 w-full whitespace-no-wrap text-sm leading-5 font-medium text-gray-900"
              >
                <div v-if="refund.status === 'Livré'" class="flex items-center space-x-3 lg:pl-2">
                  <div
                    class="flex-shrink-0 w-2.5 h-2.5 rounded-full bg-green-600"
                  ></div>
                  <div class="truncate hover:text-gray-600">
                    <span>
                      {{ refund.status }}
                    </span>
                  </div>
                </div>
                <div v-else-if="refund.status === 'En attente'" class="flex items-center space-x-3 lg:pl-2">
                  <div
                    class="flex-shrink-0 w-2.5 h-2.5 rounded-full bg-red-600"
                  ></div>
                  <div class="truncate hover:text-gray-600">
                    <span>
                      {{ refund.status }}
                    </span>
                  </div>
                </div>
                <div v-else="refund.status" class="flex items-center space-x-3 lg:pl-2">
                  <div
                    class="flex-shrink-0 w-2.5 h-2.5 rounded-full bg-yellow-600"
                  ></div>
                  <div class="truncate hover:text-gray-600">
                    <span>
                      {{ refund.status }}
                    </span>
                  </div>
                </div>
              </td>
              <td class="px-6 py-3 text-sm leading-5 text-gray-500 font-medium">

                  <div class="truncate hover:text-gray-600">
                    <span>
                      {{ refund.order.variant.product.name }}
                    </span>
                  </div>

              </td>
              <td
                class="hidden md:table-cell px-6 py-3 whitespace-no-wrap text-sm leading-5 text-gray-500 text-right"
              >
                March 17, 2020
              </td>
              <td class="pr-6">
                <div
                  class="relative flex justify-end items-center"
                >
                  <button
                    @click="idReturn(refund.id);"
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
            <!-- More project rows... -->
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
      allRefunds: null,
      viewOrderPopup: false,
      errors: [],
    };
  },
  methods: {
    idReturn(id) {
      this.id = id
    },
  },
  apollo: {
    allRefunds: {
      query: gql`
        query {
          allRefunds {
            id
            order {
              id
              variant {
                id
                sku
                product {
                  id
                  name
                }
              }
            }
          }
        }
      `
    }
  }
};
</script>
