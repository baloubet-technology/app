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
            <nuxt-link :to="{ name: 'products-id-variants', params: { id: this.$route.params.id }}" class="ml-4 px-3 py-2 font-medium text-sm leading-5 rounded-md text-gray-600 hover:text-gray-800 focus:outline-none focus:text-gray-800 focus:bg-gray-200">
              Variants
            </nuxt-link>
          </nav>
        </div>
      </div>
      <div class="mt-4 flex sm:mt-0 sm:ml-4">
        <span class="order-0 sm:order-1 sm:ml-3 shadow-sm rounded-md">
          <button
            type="button"
            class="inline-flex items-center px-4 py-2 border border-transparent text-sm leading-5 font-medium rounded-md text-white bg-purple-600 hover:bg-purple-500 focus:outline-none focus:shadow-outline-purple focus:border-purple-700 active:bg-indigo-700 transition duration-150 ease-in-out"
          >
            Edit
          </button>
        </span>
      </div>
    </div>
    <!-- Projects table (small breakpoint and up) -->
    <div class="bg-white border-b border-gray-200 overflow-hidden">
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
          <div class="sm:col-span-2">
            <dt class="text-sm leading-5 font-medium text-gray-500">
              Name
            </dt>
            <dd class="mt-1 text-sm leading-5 text-gray-900">
              {{ productId.name }}
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
              Brand
            </dt>
            <dd class="mt-1 text-sm leading-5 text-gray-900">
              {{ productId.brand.name }}
            </dd>
          </div>
          <div class="sm:col-span-2">
            <dt class="text-sm leading-5 font-medium text-gray-500">
              Category
            </dt>
            <dd class="mt-1 text-sm leading-5 text-gray-900">
              {{ productId.tag.name }}
            </dd>
          </div>
          <div class="sm:col-span-2">
            <dt class="text-sm leading-5 font-medium text-gray-500">
              Product Id
            </dt>
            <dd class="mt-1 text-sm leading-5 text-gray-900">
              {{ productId.stripeProduct }}
            </dd>
          </div>
          <div class="sm:col-span-2">
            <dt class="text-sm leading-5 font-medium text-gray-500">
              Status
            </dt>
            <dd class="mt-1 text-sm leading-5 text-gray-900">
              <span v-if="productId.status === 'Live'" class="inline-flex items-center px-2 py-0.5 rounded text-xs font-medium leading-4 bg-green-100 text-green-800">
                {{ productId.status }}
              </span>
              <span v-if="productId.status === 'Offline'" class="inline-flex items-center px-2 py-0.5 rounded text-xs font-medium leading-4 bg-purple-100 text-purple-800">
                {{ productId.status }}
              </span>
              <span v-if="productId.status === 'Pending'" class="inline-flex items-center px-2 py-0.5 rounded text-xs font-medium leading-4 bg-blue-100 text-blue-800">
                {{ productId.status }}
              </span>
              <span v-if="productId.status === 'Rejected'" class="inline-flex items-center px-2 py-0.5 rounded text-xs font-medium leading-4 bg-red-100 text-red-800">
                {{ productId.status }}
              </span>
            </dd>
          </div>
          <div class="sm:col-span-2">
            <dt class="text-sm leading-5 font-medium text-gray-500">
              Package
            </dt>
            <dd class="mt-1 text-sm leading-5 text-gray-900">
              {{ productId.package.name }}
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
            package {
              name
            }
            tag {
              name
            }
            brand {
              name
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
