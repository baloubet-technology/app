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
        <span class="order-1 ml-3 shadow-sm rounded-md sm:order-0 sm:ml-0">
          <button
            type="button"
            class="inline-flex items-center px-4 py-2 border border-gray-300 text-sm leading-5 font-medium rounded-md text-gray-700 bg-white hover:text-gray-500 focus:outline-none focus:shadow-outline-blue focus:border-blue-300 active:text-gray-800 active:bg-gray-50 transition duration-150 ease-in-out"
          >
            Share
          </button>
        </span>
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

    <!-- Projects list (only on smallest breakpoint) -->
    <div class="mt-10 sm:hidden">
      <div class="px-4 sm:px-6">
        <h2 class="text-gray-500 text-xs font-medium uppercase tracking-wide">
          Projects
        </h2>
      </div>
      <ul class="mt-3 border-t border-gray-200 divide-y divide-gray-100">
        <li>
          <a
            href="#"
            class="flex items-center justify-between px-4 py-4 hover:bg-gray-50 sm:px-6"
          >
            <div class="flex items-center truncate space-x-3">
              <div
                class="w-2.5 h-2.5 flex-shrink-0 rounded-full bg-pink-600"
              ></div>
              <p class="font-medium truncate text-sm leading-6">
                GraphQL API
                <span class="truncate font-normal text-gray-500"
                  >in Engineering</span
                >
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
            <tr class="border-t border-gray-200">
              <th
                class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
              >
                <span class="lg:pl-2">Project</span>
              </th>
              <th
                class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
              >
                Members
              </th>
              <th
                class="hidden md:table-cell px-6 py-3 border-b border-gray-200 bg-gray-50 text-right text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
              >
                Last updated
              </th>
              <th
                class="pr-6 py-3 border-b border-gray-200 bg-gray-50 text-right text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider"
              ></th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-100">
            <tr v-for="order in allOrders">
              <td
                class="px-6 py-3 max-w-0 w-full whitespace-no-wrap text-sm leading-5 font-medium text-gray-900"
              >
                <div class="flex items-center space-x-3 lg:pl-2">
                  <div
                    class="flex-shrink-0 w-2.5 h-2.5 rounded-full bg-green-600"
                  ></div>
                  <a href="#" class="truncate hover:text-gray-600">
                    <span>
                      {{ order.status }}
                    </span>
                  </a>
                </div>
              </td>
              <td class="px-6 py-3 text-sm leading-5 text-gray-500 font-medium">
                <div class="flex items-center space-x-2">
                  <div class="flex flex-shrink-0 -space-x-1">
                    <img
                      class="max-w-none h-6 w-6 rounded-full text-white shadow-solid"
                      src="https://images.unsplash.com/photo-1502685104226-ee32379fefbe?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                      alt=""
                    />

                    <img
                      class="max-w-none h-6 w-6 rounded-full text-white shadow-solid"
                      src="https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                      alt=""
                    />

                    <img
                      class="max-w-none h-6 w-6 rounded-full text-white shadow-solid"
                      src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                      alt=""
                    />

                    <img
                      class="max-w-none h-6 w-6 rounded-full text-white shadow-solid"
                      src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                      alt=""
                    />
                  </div>

                  <span class="flex-shrink-0 text-xs leading-5 font-medium"
                    >+8</span
                  >
                </div>
              </td>
              <td
                class="hidden md:table-cell px-6 py-3 whitespace-no-wrap text-sm leading-5 text-gray-500 text-right"
              >
                March 17, 2020
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
                        d="M10 6a2 2 0 110-4 2 2 0 010 4zM10 12a2 2 0 110-4 2 2 0 010 4zM10 18a2 2 0 110-4 2 2 0 010 4z"
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
      allOrders: null,
      errors: [],
    };
  },
  apollo: {
    allOrders: {
      query: gql`
        query {
          allOrders {
            id
            price
            shippingLabel
            status
            orderUrl
            variant {
              id
              product {
                name
              }
            }
          }
        }
      `
    }
  }
};
</script>
