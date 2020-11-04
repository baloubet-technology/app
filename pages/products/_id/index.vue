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
            <a href="#" class="px-3 py-2 font-medium text-sm leading-5 rounded-md text-gray-800 bg-gray-200 focus:outline-none focus:bg-gray-300" aria-current="page">
              Infos
            </a>
            <nuxt-link :to="{ name: 'products-id-variants', params: { id: 1 }}" class="ml-4 px-3 py-2 font-medium text-sm leading-5 rounded-md text-gray-600 hover:text-gray-800 focus:outline-none focus:text-gray-800 focus:bg-gray-200">
              Variants
            </nuxt-link>
            <a href="#" class="ml-4 px-3 py-2 font-medium text-sm leading-5 rounded-md text-gray-600 hover:text-gray-800 focus:outline-none focus:text-gray-800 focus:bg-gray-200">
              All Orders
            </a>
            <a href="#" class="ml-4 px-3 py-2 font-medium text-sm leading-5 rounded-md text-gray-600 hover:text-gray-800 focus:outline-none focus:text-gray-800 focus:bg-gray-200">
              Billing
            </a>
          </nav>
        </div>
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
    <!-- Projects table (small breakpoint and up) -->
    <div class="bg-white shadow overflow-hidden sm:rounded-lg">
      <div class="px-4 py-5 border-b border-gray-200 sm:px-6">
        <h3 class="text-lg leading-6 font-medium text-gray-900">
          Product Information
        </h3>
        <p class="mt-1 max-w-2xl text-sm leading-5 text-gray-500">
          Personal details and application.
        </p>
      </div>
      <div class="px-4 py-5 sm:px-6">
        <dl class="grid grid-cols-1 gap-x-4 gap-y-8 sm:grid-cols-2">
          <div class="sm:col-span-1">
            <dt class="text-sm leading-5 font-medium text-gray-500">
              Name
            </dt>
            <dd class="mt-1 text-sm leading-5 text-gray-900">
              {{ productId.name }}
            </dd>
          </div>
          <div class="sm:col-span-1">
            <dt class="text-sm leading-5 font-medium text-gray-500">
              Product Id
            </dt>
            <dd class="mt-1 text-sm leading-5 text-gray-900">
              {{ productId.stripeProduct }}
            </dd>
          </div>
          <div class="sm:col-span-1">
            <dt class="text-sm leading-5 font-medium text-gray-500">
              Email address
            </dt>
            <dd class="mt-1 text-sm leading-5 text-gray-900">
              margotfoster@example.com
            </dd>
          </div>
          <div class="sm:col-span-1">
            <dt class="text-sm leading-5 font-medium text-gray-500">
              Salary expectation
            </dt>
            <dd class="mt-1 text-sm leading-5 text-gray-900">
              $120,000
            </dd>
          </div>
          <div class="sm:col-span-2">
            <dt class="text-sm leading-5 font-medium text-gray-500">
              Description
            </dt>
            <dd class="mt-1 text-sm leading-5 text-gray-900">
              {{ productId.description }}
            </dd>
          </div>
          <div class="sm:col-span-2">
            <dt class="text-sm leading-5 font-medium text-gray-500">
              Attachments
            </dt>
            <dd class="mt-1 text-sm leading-5 text-gray-900">
              <ul class="border border-gray-200 rounded-md">
                <li class="pl-3 pr-4 py-3 flex items-center justify-between text-sm leading-5">
                  <div class="w-0 flex-1 flex items-center">
                    <!-- Heroicon name: paper-clip -->
                    <svg class="flex-shrink-0 h-5 w-5 text-gray-400" viewBox="0 0 20 20" fill="currentColor">
                      <path fill-rule="evenodd" d="M8 4a3 3 0 00-3 3v4a5 5 0 0010 0V7a1 1 0 112 0v4a7 7 0 11-14 0V7a5 5 0 0110 0v4a3 3 0 11-6 0V7a1 1 0 012 0v4a1 1 0 102 0V7a3 3 0 00-3-3z" clip-rule="evenodd" />
                    </svg>
                    <span class="ml-2 flex-1 w-0 truncate">
                      resume_back_end_developer.pdf
                    </span>
                  </div>
                  <div class="ml-4 flex-shrink-0">
                    <a href="#" class="font-medium text-indigo-600 hover:text-indigo-500 transition duration-150 ease-in-out">
                      Download
                    </a>
                  </div>
                </li>
                <li class="border-t border-gray-200 pl-3 pr-4 py-3 flex items-center justify-between text-sm leading-5">
                  <div class="w-0 flex-1 flex items-center">
                    <!-- Heroicon name: paper-clip -->
                    <svg class="flex-shrink-0 h-5 w-5 text-gray-400" viewBox="0 0 20 20" fill="currentColor">
                      <path fill-rule="evenodd" d="M8 4a3 3 0 00-3 3v4a5 5 0 0010 0V7a1 1 0 112 0v4a7 7 0 11-14 0V7a5 5 0 0110 0v4a3 3 0 11-6 0V7a1 1 0 012 0v4a1 1 0 102 0V7a3 3 0 00-3-3z" clip-rule="evenodd" />
                    </svg>
                    <span class="ml-2 flex-1 w-0 truncate">
                      coverletter_back_end_developer.pdf
                    </span>
                  </div>
                  <div class="ml-4 flex-shrink-0">
                    <a href="#" class="font-medium text-indigo-600 hover:text-indigo-500 transition duration-150 ease-in-out">
                      Download
                    </a>
                  </div>
                </li>
              </ul>
            </dd>
          </div>
        </dl>
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
            description
            stripeProduct
            status
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
