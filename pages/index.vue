<template>
  <div class="min-h-screen bg-white flex">
    <div
      class="flex-1 flex flex-col justify-center py-12 px-4 sm:px-6 lg:flex-none lg:px-20 xl:px-24"
    >
      <div class="mx-auto w-full max-w-sm lg:w-96">
        <div>
          <img
            class="h-12 w-auto"
            src="https://tailwindui.com/img/logos/workflow-mark-on-white.svg"
            alt="Workflow"
          />
          <h2 class="mt-6 text-3xl leading-9 font-extrabold text-gray-900">
            Sign in to your account
          </h2>
          <p class="mt-2 text-sm leading-5 text-gray-600 max-w">
            Or
            <a
              href="#"
              class="font-medium text-indigo-600 hover:text-indigo-500 focus:outline-none focus:underline transition ease-in-out duration-150"
            >
              start your 90-day free trial
            </a>
          </p>
        </div>

        <div class="mt-8">
          <div>

            <div class="mt-6 relative">
              <div class="absolute inset-0 flex items-center">
                <div class="w-full border-t border-gray-300"></div>
              </div>
              <div class="relative flex justify-center text-sm leading-5">
                <span class="px-2 bg-white text-gray-500">
                  Continue with
                </span>
              </div>
            </div>
          </div>

          <div class="mt-6">
            <form ref="form" @submit.prevent="signIn" class="space-y-6">
              <div>
                <label
                  for="email"
                  class="block text-sm font-medium leading-5 text-gray-700"
                >
                  Email address
                </label>
                <div class="mt-1 rounded-md shadow-sm">
                  <input
                    id="email"
                    v-model="email"
                    type="email"
                    required
                    class="appearance-none block w-full px-3 py-2 border border-gray-300 rounded-md placeholder-gray-400 focus:outline-none focus:shadow-outline-blue focus:border-blue-300 transition duration-150 ease-in-out sm:text-sm sm:leading-5"
                  />
                </div>
              </div>

              <div>
                <label
                  for="password"
                  class="block text-sm font-medium leading-5 text-gray-700"
                >
                  Password
                </label>
                <div class="mt-1 rounded-md shadow-sm">
                  <input
                    id="password"
                    v-model="password"
                    type="password"
                    required
                    class="appearance-none block w-full px-3 py-2 border border-gray-300 rounded-md placeholder-gray-400 focus:outline-none focus:shadow-outline-blue focus:border-blue-300 transition duration-150 ease-in-out sm:text-sm sm:leading-5"
                  />
                </div>
              </div>

              <div class="flex items-center justify-between">
                <div class="text-sm leading-5">
                  <a
                    href="#"
                    class="font-medium text-indigo-600 hover:text-indigo-500 focus:outline-none focus:underline transition ease-in-out duration-150"
                  >
                    Forgot your password?
                  </a>
                </div>
              </div>

              <div>
                <span class="block w-full rounded-md shadow-sm">
                  <button
                    type="submit"
                    class="w-full flex justify-center py-2 px-4 border border-transparent text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-500 focus:outline-none focus:border-indigo-700 focus:shadow-outline-indigo active:bg-indigo-700 transition duration-150 ease-in-out"
                  >
                    Sign in
                  </button>
                </span>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
    <div class="hidden lg:block relative w-0 flex-1">
      <img
        class="absolute inset-0 h-full w-full object-cover"
        src="https://images.unsplash.com/photo-1505904267569-f02eaeb45a4c?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1908&q=80"
        alt=""
      />
    </div>
  </div>
</template>

<script>
import gql from "graphql-tag";
export default {
  data() {
    return {
      email: "",
      password: "",
      errors: [],
    };
  },
  methods: {
    signIn() {
      this.$apollo
        .mutate({
          mutation: gql`
            mutation signIn($email: String!, $password: String!) {
              signIn(input: { email: $email, password: $password }) {
                member {
                  id
                  authenticationToken
                }
              }
            }
          `,
          variables: {
            email: this.email,
            password: this.password,
          },
        })
        .then((data) => {
          this.$apolloHelpers.onLogin(
            data.data.signIn.member.authenticationToken
          );
          this.$router.push("/dashboard");
        })
        .catch((e) => {
          this.errors = e.graphQLErrors;
        });
    },
  },
};
</script>
