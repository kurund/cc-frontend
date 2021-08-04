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
        <div v-if="callInfo.callerNumber" class="mt-4">
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
        <form action="#" method="POST" @submit.prevent="saveCallerInfo">
          <div class="shadow overflow-hidden sm:rounded-md">
            <div class="px-4 py-5 bg-white sm:p-6">
              <div class="grid grid-cols-6 gap-6">
                <div class="col-span-6">
                  <fieldset>
                    <div>
                      <legend class="text-base font-medium text-gray-900">
                        Caller Type
                      </legend>
                    </div>
                    <div class="mt-4 space-y-4">
                      <div class="flex flex-row">
                        <div v-for="type in callerTypes" :key="type.id">
                          <input
                            :id="type.id"
                            v-model="callerInfo.type"
                            name="callerType"
                            type="radio"
                            :value="type.id"
                            class="radio-field"
                          />
                          <label
                            :for="type.id"
                            class="ml-3 text-sm font-medium text-gray-700"
                          >
                            {{ type.label }}
                          </label>
                        </div>
                        <div v-if="callerInfo.type === 'other'" class="ml-3">
                          <input
                            id="callerTypeOther"
                            v-model="callerInfo.typeOther"
                            type="text"
                            name="callerTypeOther"
                            class="input-field"
                          />
                        </div>
                      </div>
                    </div>
                  </fieldset>
                </div>

                <div class="col-span-6">
                  <label
                    for="phoneNumber"
                    class="block text-sm font-medium text-gray-700"
                    >Phone Number</label
                  >
                  <input
                    id="phoneNumber"
                    v-model="callerInfo.phone"
                    type="text"
                    name="phoneNumber"
                    autocomplete="phone"
                    class="input-field"
                    :disabled="callInfo.callerNumber"
                    required
                  />
                </div>

                <div class="col-span-6 sm:col-span-3">
                  <label
                    for="firstName"
                    class="block text-sm font-medium text-gray-700"
                    >First name</label
                  >
                  <input
                    id="firstName"
                    v-model="callerInfo.firstName"
                    type="text"
                    name="firstName"
                    autocomplete="given-name"
                    class="input-field"
                  />
                </div>

                <div class="col-span-6 sm:col-span-3">
                  <label
                    for="lastName"
                    class="block text-sm font-medium text-gray-700"
                    >Last name</label
                  >
                  <input
                    id="lastName"
                    v-model="callerInfo.lastName"
                    type="text"
                    name="lastName"
                    autocomplete="family-name"
                    class="input-field"
                  />
                </div>

                <div class="col-span-6 sm:col-span-3">
                  <label
                    for="country"
                    class="block text-sm font-medium text-gray-700"
                    >Country</label
                  >
                  <select
                    id="country"
                    v-model="callerInfo.country"
                    name="country"
                    autocomplete="country"
                    class="select-field"
                  >
                    <option>-- please select --</option>
                    <option>India</option>
                    <option>United States</option>
                    <option>Canada</option>
                  </select>
                </div>

                <div class="col-span-6 sm:col-span-3">
                  <label
                    for="state"
                    class="block text-sm font-medium text-gray-700"
                    >State</label
                  >
                  <select
                    id="state"
                    v-model="callerInfo.state"
                    name="state"
                    autocomplete="state"
                    class="select-field"
                  >
                    <option>-- please select --</option>
                    <option>Tamil Nadu</option>
                    <option>Karnataka</option>
                  </select>
                </div>

                <div class="col-span-6 sm:col-span-3">
                  <label
                    for="district"
                    class="block text-sm font-medium text-gray-700"
                    >District</label
                  >
                  <select
                    id="district"
                    v-model="callerInfo.district"
                    name="district"
                    autocomplete="district"
                    class="select-field"
                  >
                    <option>-- please select --</option>
                    <option>District 1</option>
                    <option>District 2</option>
                  </select>
                </div>

                <div class="col-span-6 sm:col-span-3">
                  <label
                    for="taluka"
                    class="block text-sm font-medium text-gray-700"
                    >Taluka</label
                  >
                  <select
                    id="taluka"
                    v-model="callerInfo.taluka"
                    name="taluka"
                    autocomplete="taluka"
                    class="select-field"
                  >
                    <option>-- please select --</option>
                    <option>Taluka 1</option>
                    <option>Taluka 2</option>
                  </select>
                </div>

                <div class="col-span-6 sm:col-span-3">
                  <label
                    for="village"
                    class="block text-sm font-medium text-gray-700"
                    >Village</label
                  >
                  <select
                    id="village"
                    v-model="callerInfo.village"
                    name="village"
                    autocomplete="village"
                    class="select-field"
                  >
                    <option>-- please select --</option>
                    <option>Village 1</option>
                    <option>Village 2</option>
                    <option>Other</option>
                  </select>
                </div>

                <div
                  v-if="callerInfo.village === 'Other'"
                  class="col-span-6 sm:col-span-3"
                >
                  <label
                    for="villageOther"
                    class="block text-sm font-medium text-gray-700"
                    >Village Name</label
                  >
                  <input
                    id="otherVillage"
                    v-model="callerInfo.otherVillage"
                    type="text"
                    name="otherVillage"
                    class="input-field"
                  />
                </div>

                <!-- <div class="col-span-6">
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
                </div> -->

                <!-- <div class="col-span-6 sm:col-span-6 lg:col-span-2">
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
                </div> -->
              </div>
            </div>
            <div class="px-4 py-3 bg-gray-50 text-right sm:px-6">
              <button type="submit" class="purple-button">Save</button>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import callerTypes from '../data/constants'

export default {
  data() {
    return {
      callerTypes,
      callInfo: [],
      callerInfo: {
        type: 'farmer',
        typeOther: '',
        firstName: '',
        lastName: '',
        phone: '',
        email: '',
        country: '',
        state: '',
        district: '',
        taluka: '',
        village: '',
        otherVillage: '',
      },
    }
  },
  methods: {
    getCallDetails() {
      this.callInfo = {
        callerNumber: '9989889887',
        optionSelected: '1',
      }
      this.callerInfo.phone = this.callInfo.callerNumber
      return this.callInfo
    },
    callDone() {
      this.callInfo = []
    },
    saveCallerInfo() {
      console.log(this.callerInfo)
    },
  },
}
</script>

<style scoped></style>
