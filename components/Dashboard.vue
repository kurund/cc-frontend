<template>
  <div class="container">
    <div class="max-w-4xl mx-auto sm:px-6 lg:px-8">
      <div class="mt-8 bg-white overflow-hidden shadow sm:rounded-lg p-6">
        <div class="flex items-center">
          <div class="flex-grow">
            <h2 class="text-2xl leading-7 font-semibold">
              IVR Live Call Details
            </h2>
          </div>
          <div class="justify-end">
            <button class="green-button" @click="getCallDetails">
              Refresh
            </button>
          </div>
        </div>
        <div class="mt-4" v-if="callInfo.callerNumber">
          <div class="mb-4">
            <div class="leading-5 font-semibold mb-4">
              <span class="font-semibold"> Caller Number: </span>
              <span>
                {{ callInfo.callerNumber }}
              </span>
            </div>
            <div class="leading-5 font-semibold">
              <span class="leading-5 font-semibold"> Options Selected: </span>
              <span>
                {{ callInfo.optionSelected }}
              </span>
            </div>

            <div class="mt-4">
              <button class="blue-button" @click="callDone">Done</button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="max-w-4xl mx-auto sm:px-6 lg:px-8 mt-8">
      <div class="mt-5 md:mt-0 md:col-span-2">
        <form action="#" method="POST">
          <div class="shadow overflow-hidden sm:rounded-md">
            <div class="px-4 py-5 bg-white sm:p-6">
              <div class="grid grid-cols-6 gap-6">
                <div class="col-span-6 sm:col-span-6">
                  <fieldset>
                    <div>
                      <legend class="text-base font-medium text-gray-900">
                        Caller Type
                      </legend>
                    </div>
                    <div class="mt-4 space-y-4">
                      <div class="flex flex-row">
                        <div class="">
                          <input
                            id="callerType"
                            name="push-notifications"
                            type="radio"
                            class="
                              focus:ring-indigo-500
                              h-4
                              w-4
                              text-indigo-600
                              border-gray-300
                            "
                          />
                          <label
                            for="Farmer"
                            class="ml-3 block text-sm font-medium text-gray-700"
                          >
                            Farmer
                          </label>
                        </div>
                        <div class="">
                          <input
                            id="callerType"
                            name="push-notifications"
                            type="radio"
                            class="
                              focus:ring-indigo-500
                              h-4
                              w-4
                              text-indigo-600
                              border-gray-300
                            "
                          />
                          <label
                            for="push-everything"
                            class="ml-3 block text-sm font-medium text-gray-700"
                          >
                            Everything
                          </label>
                        </div>
                        <div class="">
                          <input
                            id="callerType"
                            name="push-notifications"
                            type="radio"
                            class="
                              focus:ring-indigo-500
                              h-4
                              w-4
                              text-indigo-600
                              border-gray-300
                            "
                          />
                          <label
                            for="push-everything"
                            class="ml-3 block text-sm font-medium text-gray-700"
                          >
                            Everything
                          </label>
                        </div>
                      </div>
                      <div class="flex items-center">
                        <input
                          id="push-email"
                          name="push-notifications"
                          type="radio"
                          class="
                            focus:ring-indigo-500
                            h-4
                            w-4
                            text-indigo-600
                            border-gray-300
                          "
                        />
                        <label
                          for="push-email"
                          class="ml-3 block text-sm font-medium text-gray-700"
                        >
                          Same as email
                        </label>
                      </div>
                      <div class="flex items-center">
                        <input
                          id="push-nothing"
                          name="push-notifications"
                          type="radio"
                          class="
                            focus:ring-indigo-500
                            h-4
                            w-4
                            text-indigo-600
                            border-gray-300
                          "
                        />
                        <label
                          for="push-nothing"
                          class="ml-3 block text-sm font-medium text-gray-700"
                        >
                          No push notifications
                        </label>
                      </div>
                    </div>
                  </fieldset>
                </div>
                <div class="col-span-6 sm:col-span-3">
                  <label
                    for="first-name"
                    class="block text-sm font-medium text-gray-700"
                    >First name</label
                  >
                  <input
                    type="text"
                    name="first-name"
                    id="first-name"
                    autocomplete="given-name"
                    class="
                      mt-1
                      focus:ring-indigo-500
                      focus:border-indigo-500
                      block
                      w-full
                      shadow-sm
                      sm:text-sm
                      border-gray-300
                      rounded-md
                    "
                  />
                </div>

                <div class="col-span-6 sm:col-span-3">
                  <label
                    for="last-name"
                    class="block text-sm font-medium text-gray-700"
                    >Last name</label
                  >
                  <input
                    type="text"
                    name="last-name"
                    id="last-name"
                    autocomplete="family-name"
                    class="
                      mt-1
                      focus:ring-indigo-500
                      focus:border-indigo-500
                      block
                      w-full
                      shadow-sm
                      sm:text-sm
                      border-gray-300
                      rounded-md
                    "
                  />
                </div>

                <div class="col-span-6 sm:col-span-4">
                  <label
                    for="email-address"
                    class="block text-sm font-medium text-gray-700"
                    >Email address</label
                  >
                  <input
                    type="text"
                    name="email-address"
                    id="email-address"
                    autocomplete="email"
                    class="
                      mt-1
                      focus:ring-indigo-500
                      focus:border-indigo-500
                      block
                      w-full
                      shadow-sm
                      sm:text-sm
                      border-gray-300
                      rounded-md
                    "
                  />
                </div>

                <div class="col-span-6 sm:col-span-3">
                  <label
                    for="country"
                    class="block text-sm font-medium text-gray-700"
                    >Country / Region</label
                  >
                  <select
                    id="country"
                    name="country"
                    autocomplete="country"
                    class="
                      mt-1
                      block
                      w-full
                      py-2
                      px-3
                      border border-gray-300
                      bg-white
                      rounded-md
                      shadow-sm
                      focus:outline-none
                      focus:ring-indigo-500
                      focus:border-indigo-500
                      sm:text-sm
                    "
                  >
                    <option>United States</option>
                    <option>Canada</option>
                    <option>Mexico</option>
                  </select>
                </div>

                <div class="col-span-6">
                  <label
                    for="street-address"
                    class="block text-sm font-medium text-gray-700"
                    >Street address</label
                  >
                  <input
                    type="text"
                    name="street-address"
                    id="street-address"
                    autocomplete="street-address"
                    class="
                      mt-1
                      focus:ring-indigo-500
                      focus:border-indigo-500
                      block
                      w-full
                      shadow-sm
                      sm:text-sm
                      border-gray-300
                      rounded-md
                    "
                  />
                </div>

                <div class="col-span-6 sm:col-span-6 lg:col-span-2">
                  <label
                    for="city"
                    class="block text-sm font-medium text-gray-700"
                    >City</label
                  >
                  <input
                    type="text"
                    name="city"
                    id="city"
                    class="
                      mt-1
                      focus:ring-indigo-500
                      focus:border-indigo-500
                      block
                      w-full
                      shadow-sm
                      sm:text-sm
                      border-gray-300
                      rounded-md
                    "
                  />
                </div>

                <div class="col-span-6 sm:col-span-3 lg:col-span-2">
                  <label
                    for="state"
                    class="block text-sm font-medium text-gray-700"
                    >State / Province</label
                  >
                  <input
                    type="text"
                    name="state"
                    id="state"
                    class="
                      mt-1
                      focus:ring-indigo-500
                      focus:border-indigo-500
                      block
                      w-full
                      shadow-sm
                      sm:text-sm
                      border-gray-300
                      rounded-md
                    "
                  />
                </div>

                <div class="col-span-6 sm:col-span-3 lg:col-span-2">
                  <label
                    for="postal-code"
                    class="block text-sm font-medium text-gray-700"
                    >ZIP / Postal</label
                  >
                  <input
                    type="text"
                    name="postal-code"
                    id="postal-code"
                    autocomplete="postal-code"
                    class="
                      mt-1
                      focus:ring-indigo-500
                      focus:border-indigo-500
                      block
                      w-full
                      shadow-sm
                      sm:text-sm
                      border-gray-300
                      rounded-md
                    "
                  />
                </div>
              </div>
            </div>
            <div class="px-4 py-3 bg-gray-50 text-right sm:px-6">
              <button
                type="submit"
                class="
                  inline-flex
                  justify-center
                  py-2
                  px-4
                  border border-transparent
                  shadow-sm
                  text-sm
                  font-medium
                  rounded-md
                  text-white
                  bg-indigo-600
                  hover:bg-indigo-700
                  focus:outline-none
                  focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500
                "
              >
                Save
              </button>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      callInfo: [],
      callerInfo: {
        name: '',
      },
    }
  },
  methods: {
    getCallDetails() {
      this.callInfo = {
        callerNumber: '9989889887',
        optionSelected: '1',
      }
      return this.callInfo
    },
    callDone() {
      this.callInfo = []
    },
  },
}
</script>

<style scoped>
</style>