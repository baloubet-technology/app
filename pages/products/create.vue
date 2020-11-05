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

        <form>
          <div>
            <div>
              <div>
                <h3 class="text-lg leading-6 font-medium text-gray-900">
                  Personal Information
                </h3>
                <p class="mt-1 text-sm leading-5 text-gray-500">
                  Use a permanent address where you can receive mail.
                </p>
              </div>
              <div class="mt-6 grid grid-cols-1 gap-y-6 gap-x-4 sm:grid-cols-6">
                <div class="sm:col-span-3">
                  <label for="first_name" class="block text-sm font-medium leading-5 text-gray-700">
                    Name
                  </label>
                  <div class="mt-1 rounded-md shadow-sm">
                    <input v-model="product.name" id="first_name" class="form-input block w-full transition duration-150 ease-in-out sm:text-sm sm:leading-5">
                  </div>
                </div>

                <div class="sm:col-span-3">
                  <label for="last_name" class="block text-sm font-medium leading-5 text-gray-700">
                    Description
                  </label>
                  <div class="mt-1 rounded-md shadow-sm">
                    <input v-model="product.description" id="last_name" class="form-input block w-full transition duration-150 ease-in-out sm:text-sm sm:leading-5">
                  </div>
                </div>

                <div class="sm:col-span-4">
                  <label for="email" class="block text-sm font-medium leading-5 text-gray-700">
                    Brands
                  </label>
                  <select v-model="product.brandId" id="location" class="mt-1 form-select block w-full pl-3 pr-10 py-2 text-base leading-6 border-gray-300 focus:outline-none focus:shadow-outline-blue focus:border-blue-300 sm:text-sm sm:leading-5">
                    <option v-for="brand in brands" :key="brand.id" :value="brand.id" >{{ brand.name }}</option>
                  </select>
                </div>

                <div class="sm:col-span-3">
                  <label for="country" class="block text-sm font-medium leading-5 text-gray-700">
                    Tags
                  </label>
                  <div class="mt-1 rounded-md shadow-sm">
                    <select v-model="product.tagId" id="country" class="form-select block w-full transition duration-150 ease-in-out sm:text-sm sm:leading-5">
                      <option v-for="tag in tags" :key="tag.id" :value="tag.id" >{{ tag.name }}</option>
                    </select>
                  </div>
                </div>

                <div class="sm:col-span-2">
                  <label for="city" class="block text-sm font-medium leading-5 text-gray-700">
                    Packages
                  </label>
                  <select v-model="product.packageId" id="location" class="mt-1 form-select block w-full pl-3 pr-10 py-2 text-base leading-6 border-gray-300 focus:outline-none focus:shadow-outline-blue focus:border-blue-300 sm:text-sm sm:leading-5">
                    <option v-for="pack in packs" :key="pack.id" :value="pack.id" >{{ pack.name }}</option>
                  </select>
                </div>

              </div>
            </div>
          </div>
          <div class="mt-8 border-t border-gray-200 pt-5">
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
      product: null,
      brands: null,
      tags: null,
      packs: null,
      errors: [],
    };
  },
  methods: {
    createProduct() {
      this.$apollo
        .mutate({
          mutation: gql`
            mutation createProduct($name: String!, $description: String!, $brandId: Integer!, $tagId: Integer!, $packageId: Integer!) {
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
          this.$router.push("/products");
        })
        .catch((e) => {
          this.errors = e.graphQLErrors;
        });
    },
  },
  apollo: {
    brands: {
      query: gql`
        query {
          brands {
            id
            name
          }
        }
      `
    },
    tags: {
      query: gql`
        query {
          tags {
            id
            name
          }
        }
      `
    },
    packs: {
      query: gql`
        query {
          packages {
            id
            name
          }
        }
      `
    }
  },
};
</script>
