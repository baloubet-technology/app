<template>
  <form>
    <div v-if="step === 1" class="lg:border-t lg:border-b lg:border-gray-200">
      <nav class="mx-auto max-w-screen-xl px-4 sm:px-6 lg:px-8">
        <ul class="rounded-md overflow-hidden lg:flex lg:border-l lg:border-r lg:border-gray-200 lg:rounded-none">
          <li class="relative overflow-hidden lg:flex-1">
            <div class="border border-gray-200 overflow-hidden border-b-0 rounded-t-md lg:border-0">
              <!-- Completed Step -->
              <a href="#" class="group">
                <div class="absolute top-0 left-0 w-1 h-full bg-transparent group-hover:bg-gray-200 group-focus:bg-gray-200 lg:w-full lg:h-1 lg:bottom-0 lg:top-auto"></div>
                <div class="px-6 py-5 flex items-start text-sm leading-5 font-medium space-x-4">
                  <div class="flex-shrink-0">
                    <div class="w-10 h-10 flex items-center justify-center bg-indigo-600 rounded-full">
                      <!-- Heroicon name: check -->
                      <svg class="w-6 h-6 text-white" viewBox="0 0 20 20" fill="currentColor">
                        <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                      </svg>
                    </div>
                  </div>
                  <div class="mt-0.5 min-w-0">
                    <h3 class="text-xs leading-4 font-semibold uppercase tracking-wide">Job Details</h3>
                    <p class="text-sm leading-5 font-medium text-gray-500">Vitae sed mi luctus laoreet.</p>
                  </div>
                </div>
              </a>
            </div>
          </li>

          <li class="relative overflow-hidden lg:flex-1">
            <div class="border border-gray-200 overflow-hidden lg:border-0">
              <!-- Current Step -->
              <div class="absolute top-0 left-0 w-1 h-full bg-indigo-600 lg:w-full lg:h-1 lg:bottom-0 lg:top-auto"></div>
              <div class="px-6 py-5 flex items-start text-sm leading-5 font-medium space-x-4 lg:pl-9">
                <div class="flex-shrink-0">
                  <div class="w-10 h-10 flex items-center justify-center border-2 border-indigo-600 rounded-full">
                    <p class="text-indigo-600">02</p>
                  </div>
                </div>
                <div class="mt-0.5 min-w-0">
                  <h3 class="text-xs leading-4 font-semibold text-indigo-600 uppercase tracking-wide">Application form</h3>
                  <p class="text-sm leading-5 font-medium text-gray-500">Cursus semper viverra.</p>
                </div>
              </div>

              <div class="hidden absolute top-0 left-0 w-3 inset-0 lg:block">
                <svg class="h-full w-full text-gray-300" viewBox="0 0 12 82" fill="none" preserveAspectRatio="none">
                  <path d="M0.5 0V31L10.5 41L0.5 51V82" stroke="currentcolor" vector-effect="non-scaling-stroke" />
                </svg>
              </div>
            </div>
          </li>

          <li class="relative overflow-hidden lg:flex-1">
            <div class="border border-gray-200 overflow-hidden border-t-0 rounded-b-md lg:border-0">
              <!-- Upcoming Step -->
              <a href="#" class="group">
                <div class="absolute top-0 left-0 w-1 h-full bg-transparent group-hover:bg-gray-200 group-focus:bg-gray-200 lg:w-full lg:h-1 lg:bottom-0 lg:top-auto"></div>
                <div class="px-6 py-5 flex items-start text-sm leading-5 font-medium space-x-4 lg:pl-9">
                  <div class="flex-shrink-0">
                    <div class="w-10 h-10 flex items-center justify-center border-2 border-gray-300 rounded-full">
                      <p class="text-gray-500">03</p>
                    </div>
                  </div>
                  <div class="mt-0.5 min-w-0">
                    <h3 class="text-xs leading-4 font-semibold text-gray-500 uppercase tracking-wide">Preview</h3>
                    <p class="text-sm leading-5 font-medium text-gray-500">Penatibus eu quis ante.</p>
                  </div>
                </div>
              </a>

              <div class="hidden absolute top-0 left-0 w-3 inset-0 lg:block">
                <svg class="h-full w-full text-gray-300" viewBox="0 0 12 82" fill="none" preserveAspectRatio="none">
                  <path d="M0.5 0V31L10.5 41L0.5 51V82" stroke="currentcolor" vector-effect="non-scaling-stroke" />
                </svg>
              </div>
            </div>
          </li>
        </ul>
      </nav>

      <button @click.prevent="next()">Next</button>
    </div>



    <div v-if="step === 2" class="lg:border-t lg:border-b lg:border-gray-200">
      <nav class="mx-auto max-w-screen-xl px-4 sm:px-6 lg:px-8">
        <ul class="rounded-md overflow-hidden lg:flex lg:border-l lg:border-r lg:border-gray-200 lg:rounded-none">
          <li class="relative overflow-hidden lg:flex-1">
            <div class="border border-gray-200 overflow-hidden border-b-0 rounded-t-md lg:border-0">
              <!-- Completed Step -->
              <a href="#" class="group">
                <div class="absolute top-0 left-0 w-1 h-full bg-transparent group-hover:bg-gray-200 group-focus:bg-gray-200 lg:w-full lg:h-1 lg:bottom-0 lg:top-auto"></div>
                <div class="px-6 py-5 flex items-start text-sm leading-5 font-medium space-x-4">
                  <div class="flex-shrink-0">
                    <div class="w-10 h-10 flex items-center justify-center bg-indigo-600 rounded-full">
                      <!-- Heroicon name: check -->
                      <svg class="w-6 h-6 text-white" viewBox="0 0 20 20" fill="currentColor">
                        <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                      </svg>
                    </div>
                  </div>
                  <div class="mt-0.5 min-w-0">
                    <h3 class="text-xs leading-4 font-semibold uppercase tracking-wide">Job Details</h3>
                    <p class="text-sm leading-5 font-medium text-gray-500">Vitae sed mi luctus laoreet.</p>
                  </div>
                </div>
              </a>
            </div>
          </li>

          <li class="relative overflow-hidden lg:flex-1">
            <div class="border border-gray-200 overflow-hidden lg:border-0">
              <!-- Current Step -->
              <div class="absolute top-0 left-0 w-1 h-full bg-indigo-600 lg:w-full lg:h-1 lg:bottom-0 lg:top-auto"></div>
              <div class="px-6 py-5 flex items-start text-sm leading-5 font-medium space-x-4 lg:pl-9">
                <div class="flex-shrink-0">
                  <div class="w-10 h-10 flex items-center justify-center border-2 border-indigo-600 rounded-full">
                    <p class="text-indigo-600">02</p>
                  </div>
                </div>
                <div class="mt-0.5 min-w-0">
                  <h3 class="text-xs leading-4 font-semibold text-indigo-600 uppercase tracking-wide">Application form</h3>
                  <p class="text-sm leading-5 font-medium text-gray-500">Cursus semper viverra.</p>
                </div>
              </div>

              <div class="hidden absolute top-0 left-0 w-3 inset-0 lg:block">
                <svg class="h-full w-full text-gray-300" viewBox="0 0 12 82" fill="none" preserveAspectRatio="none">
                  <path d="M0.5 0V31L10.5 41L0.5 51V82" stroke="currentcolor" vector-effect="non-scaling-stroke" />
                </svg>
              </div>
            </div>
          </li>

          <li class="relative overflow-hidden lg:flex-1">
            <div class="border border-gray-200 overflow-hidden border-t-0 rounded-b-md lg:border-0">
              <!-- Upcoming Step -->
              <a href="#" class="group">
                <div class="absolute top-0 left-0 w-1 h-full bg-transparent group-hover:bg-gray-200 group-focus:bg-gray-200 lg:w-full lg:h-1 lg:bottom-0 lg:top-auto"></div>
                <div class="px-6 py-5 flex items-start text-sm leading-5 font-medium space-x-4 lg:pl-9">
                  <div class="flex-shrink-0">
                    <div class="w-10 h-10 flex items-center justify-center border-2 border-gray-300 rounded-full">
                      <p class="text-gray-500">03</p>
                    </div>
                  </div>
                  <div class="mt-0.5 min-w-0">
                    <h3 class="text-xs leading-4 font-semibold text-gray-500 uppercase tracking-wide">Preview</h3>
                    <p class="text-sm leading-5 font-medium text-gray-500">Penatibus eu quis ante.</p>
                  </div>
                </div>
              </a>

              <div class="hidden absolute top-0 left-0 w-3 inset-0 lg:block">
                <svg class="h-full w-full text-gray-300" viewBox="0 0 12 82" fill="none" preserveAspectRatio="none">
                  <path d="M0.5 0V31L10.5 41L0.5 51V82" stroke="currentcolor" vector-effect="non-scaling-stroke" />
                </svg>
              </div>
            </div>
          </li>
        </ul>
      </nav>

      <button @click.prevent="prev()">Previous</button>
      <button @click.prevent="next()">Next</button>
    </div>



    <div v-if="step === 3" class="lg:border-t lg:border-b lg:border-gray-200">
      <nav class="mx-auto max-w-screen-xl px-4 sm:px-6 lg:px-8">
        <ul class="rounded-md overflow-hidden lg:flex lg:border-l lg:border-r lg:border-gray-200 lg:rounded-none">
          <li class="relative overflow-hidden lg:flex-1">
            <div class="border border-gray-200 overflow-hidden border-b-0 rounded-t-md lg:border-0">
              <!-- Completed Step -->
              <a href="#" class="group">
                <div class="absolute top-0 left-0 w-1 h-full bg-transparent group-hover:bg-gray-200 group-focus:bg-gray-200 lg:w-full lg:h-1 lg:bottom-0 lg:top-auto"></div>
                <div class="px-6 py-5 flex items-start text-sm leading-5 font-medium space-x-4">
                  <div class="flex-shrink-0">
                    <div class="w-10 h-10 flex items-center justify-center bg-indigo-600 rounded-full">
                      <!-- Heroicon name: check -->
                      <svg class="w-6 h-6 text-white" viewBox="0 0 20 20" fill="currentColor">
                        <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
                      </svg>
                    </div>
                  </div>
                  <div class="mt-0.5 min-w-0">
                    <h3 class="text-xs leading-4 font-semibold uppercase tracking-wide">Job Details</h3>
                    <p class="text-sm leading-5 font-medium text-gray-500">Vitae sed mi luctus laoreet.</p>
                  </div>
                </div>
              </a>
            </div>
          </li>

          <li class="relative overflow-hidden lg:flex-1">
            <div class="border border-gray-200 overflow-hidden lg:border-0">
              <!-- Current Step -->
              <div class="absolute top-0 left-0 w-1 h-full bg-indigo-600 lg:w-full lg:h-1 lg:bottom-0 lg:top-auto"></div>
              <div class="px-6 py-5 flex items-start text-sm leading-5 font-medium space-x-4 lg:pl-9">
                <div class="flex-shrink-0">
                  <div class="w-10 h-10 flex items-center justify-center border-2 border-indigo-600 rounded-full">
                    <p class="text-indigo-600">02</p>
                  </div>
                </div>
                <div class="mt-0.5 min-w-0">
                  <h3 class="text-xs leading-4 font-semibold text-indigo-600 uppercase tracking-wide">Application form</h3>
                  <p class="text-sm leading-5 font-medium text-gray-500">Cursus semper viverra.</p>
                </div>
              </div>

              <div class="hidden absolute top-0 left-0 w-3 inset-0 lg:block">
                <svg class="h-full w-full text-gray-300" viewBox="0 0 12 82" fill="none" preserveAspectRatio="none">
                  <path d="M0.5 0V31L10.5 41L0.5 51V82" stroke="currentcolor" vector-effect="non-scaling-stroke" />
                </svg>
              </div>
            </div>
          </li>

          <li class="relative overflow-hidden lg:flex-1">
            <div class="border border-gray-200 overflow-hidden border-t-0 rounded-b-md lg:border-0">
              <!-- Upcoming Step -->
              <a href="#" class="group">
                <div class="absolute top-0 left-0 w-1 h-full bg-transparent group-hover:bg-gray-200 group-focus:bg-gray-200 lg:w-full lg:h-1 lg:bottom-0 lg:top-auto"></div>
                <div class="px-6 py-5 flex items-start text-sm leading-5 font-medium space-x-4 lg:pl-9">
                  <div class="flex-shrink-0">
                    <div class="w-10 h-10 flex items-center justify-center border-2 border-gray-300 rounded-full">
                      <p class="text-gray-500">03</p>
                    </div>
                  </div>
                  <div class="mt-0.5 min-w-0">
                    <h3 class="text-xs leading-4 font-semibold text-gray-500 uppercase tracking-wide">Preview</h3>
                    <p class="text-sm leading-5 font-medium text-gray-500">Penatibus eu quis ante.</p>
                  </div>
                </div>
              </a>

              <div class="hidden absolute top-0 left-0 w-3 inset-0 lg:block">
                <svg class="h-full w-full text-gray-300" viewBox="0 0 12 82" fill="none" preserveAspectRatio="none">
                  <path d="M0.5 0V31L10.5 41L0.5 51V82" stroke="currentcolor" vector-effect="non-scaling-stroke" />
                </svg>
              </div>
            </div>
          </li>
        </ul>
      </nav>

      <button @click.prevent="prev()">Previous</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      step: 1,
    };
  },
  methods:{
    prev() {
      this.step--;
    },
    next() {
      this.step++;
    },
    submit() {
      alert('Submit to blah and show blah and etc.');
    }
  },
};
</script>
