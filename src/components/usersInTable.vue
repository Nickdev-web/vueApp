<template>
  <main
    class="flex-1 relative overflow-y-auto focus:outline-none"
    tabindex="0"
    id="main"
  >
    <div class="py-6">
      <div class="max-w-8xl mx-auto px-4 sm:px-6 md:px-8">
        <h1 class="text-2xl font-semibold text-gray-900">
          {{ title }} ({{ usersBase.length }}) on {{ currentDateTime() }}
        </h1>
      </div>
      <div class="max-w-8xl mx-auto px-4 sm:px-6 md:px-8">
        <div v-if="show">
          <div class="space-y-8 divide-y divide-gray-200 sm:space-y-5 w-full">
            <div class="pt-8 space-y-6 sm:pt-5 sm:space-y-5">
              <div>
                <h3 class="text-lg leading-6 font-medium text-gray-900">
                  Personal Information
                </h3>
                <p class="mt-1 max-w-2xl text-sm text-gray-500">
                  Use a permanent address where you can receive mail.
                </p>
              </div>
              <div class="space-y-6 sm:space-y-5">
                <div
                  class="sm:grid sm:grid-cols-4 sm:gap-4 sm:items-start sm:border-t sm:border-gray-200 sm:pt-5"
                >
                  <label
                    for="first_name"
                    class="block text-sm font-medium text-gray-700 sm:mt-px sm:pt-2"
                  >
                    First name
                  </label>
                  <div class="mt-1 sm:mt-0 sm:col-span-2">
                    <input
                      type="text"
                      v-model="newUserName"
                      name="first_name"
                      id="first_name"
                      class="mt-1 block w-5/12 border-none bg-white-100 h-10 p-5 rounded-xl shadow focus:outline-none hover:bg-white-200 focus:bg-white-100 focus:ring-0"
                    />
                  </div>
                </div>

                <div
                  class="sm:grid sm:grid-cols-4 sm:gap-4 sm:items-start sm:border-t sm:border-gray-200 sm:pt-5"
                >
                  <label
                    for="last_name"
                    class="block text-sm font-medium text-gray-700 sm:mt-px sm:pt-2"
                  >
                    Last name
                  </label>
                  <div class="mt-1 sm:mt-0 sm:col-span-2">
                    <input
                      v-model="newUserLastName"
                      type="text"
                      name="last_name"
                      id="last_name"
                      class="mt-1 block w-5/12 border-none bg-white-100 h-10 p-5 rounded-xl shadow focus:outline-none hover:bg-white-200 focus:bg-white-100 focus:ring-0"
                    />
                  </div>
                </div>

                <div
                  class="sm:grid sm:grid-cols-4 sm:gap-4 sm:items-start sm:border-t sm:border-gray-200 sm:pt-5"
                >
                  <label
                    for="email"
                    class="block text-sm font-medium text-gray-700 sm:mt-px sm:pt-2"
                  >
                    E-mail
                  </label>
                  <div class="mt-1 sm:mt-0 sm:col-span-2">
                    <input
                      v-model="newUserEmail"
                      type="email"
                      name="email"
                      id="email"
                      class="mt-1 block w-5/12 border-none bg-white-100 h-10 p-5 rounded-xl shadow focus:outline-none hover:bg-white-200 focus:bg-white-100 focus:ring-0"
                    />
                  </div>
                </div>
                <div
                  class="sm:grid sm:grid-cols-4 sm:gap-4 sm:items-start sm:border-t sm:border-gray-200 sm:pt-5"
                >
                  <label
                    for="email"
                    class="block text-sm font-medium text-gray-700 sm:mt-px sm:pt-2"
                  >
                    Country
                  </label>
                  <div class="mt-1 sm:mt-0 sm:col-span-2">
                    <input
                      v-model="newUserCountry"
                      type="country"
                      name="country"
                      id="country"
                      class="mt-1 block w-5/12 border-none bg-white-100 h-10 p-5 rounded-xl shadow focus:outline-none hover:bg-white-200 focus:bg-white-100 focus:ring-0"
                    />
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="pt-5 pb-10">
            <div class="flex justify-start">
              <button
                type="button"
                @click="hideUserAddTool()"
                class="bg-white py-2 px-4 border border-gray-300 rounded-md shadow-sm text-sm font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
              >
                Cancel
              </button>
              <button
                @click="
                  addNewUser(
                    newUserName,
                    newUserLastName,
                    newUserEmail,
                    newUserCountry
                  )
                "
                type="submit"
                class="ml-3 inline-flex justify-center py-2 px-4 border border-transparent shadow-sm text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
              >
                Save
              </button>
            </div>
          </div>
        </div>
        <button
          v-if="hide"
          type="button"
          @click="showUserAddTool()"
          class="inline-flex items-center mt-5 mb-5 px-3.5 py-2 border border-transparent text-sm leading-4 font-medium rounded-full shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
        >
          <svg
            class="h-5 w-5"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 20 20"
            fill="currentColor"
            aria-hidden="true"
          >
            <path
              fill-rule="evenodd"
              d="M10 5a1 1 0 011 1v3h3a1 1 0 110 2h-3v3a1 1 0 11-2 0v-3H6a1 1 0 110-2h3V6a1 1 0 011-1z"
              clip-rule="evenodd"
            />
          </svg>
          Add new user
        </button>
      </div>

      <div class="max-w-8xl mx-auto px-4 sm:px-6 md:px-8"></div>
      <div class="max-w-8xl mx-auto px-4 sm:px-6 md:px-8">
        <!-- Replace with your content -->
        <div class="py-4">
          <div class="flex flex-col">
            <div class="-my-2 overflow-x-auto w-full">
              <div class="align-middle inline-block min-w-full sm:px-6 lg:px-0">
                <div
                  class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg"
                >
                  <table class="min-w-full divide-y divide-gray-200">
                    <thead class="bg-gray-50">
                      <tr>
                        <th
                          scope="col"
                          class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                        >
                          <a
                            @click="sort('id')"
                            class="pointer"
                            v-bind:class="[
                              sortBy === 'id' ? sortDirection : '',
                            ]"
                            >Id</a
                          >
                        </th>
                        <th
                          scope="col"
                          class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                        >
                          <a
                            @click="sort('first_name')"
                            class="pointer"
                            v-bind:class="[
                              sortBy === 'first_name' ? sortDirection : '',
                            ]"
                          >
                            Name</a
                          >
                        </th>
                        <th
                          scope="col"
                          class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                        >
                          <a
                            @click="sort('last_name')"
                            class="pointer"
                            v-bind:class="[
                              sortBy === 'last_name' ? sortDirection : '',
                            ]"
                          >
                            Surname
                          </a>
                        </th>
                        <th
                          scope="col"
                          class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                        >
                          <a
                            @click="sort('email')"
                            class="pointer"
                            v-bind:class="[
                              sortBy === 'email' ? sortDirection : '',
                            ]"
                          >
                            Email
                          </a>
                        </th>
                        <th
                          scope="col"
                          class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                        >
                          <a
                            @click="sort('country')"
                            class="pointer"
                            v-bind:class="[
                              sortBy === 'country' ? sortDirection : '',
                            ]"
                          >
                            Country
                          </a>
                        </th>
                        <th
                          scope="col"
                          class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                        >
                          <a
                            @click="sort('modified')"
                            class="pointer"
                            v-bind:class="[
                              sortBy === 'modified' ? sortDirection : '',
                            ]"
                          >
                            Modified on
                          </a>
                        </th>
                        <th
                          scope="col"
                          class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider"
                        >
                          <a
                            @click="sort('status')"
                            class="pointer"
                            v-bind:class="[
                              sortBy === 'status' ? sortDirection : '',
                            ]"
                          >
                            User Status
                          </a>
                        </th>
                        <th scope="col" class="relative px-6 py-3"></th>
                        <th scope="col" class="relative px-6 py-3"></th>
                      </tr>
                    </thead>
                    <tbody
                      class="bg-white divide-y divide-gray-200"
                      v-for="(user, index) in usersBase"
                      :key="user.id"
                    >
                      <tr v-if="!usersBase[index].editable">
                        <td
                          class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900"
                        >
                          {{ user.id }}
                        </td>
                        <td
                          class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900"
                        >
                          {{ user.first_name }}
                        </td>
                        <td
                          class="px-6 py-4 whitespace-nowrap text-sm text-gray-500"
                        >
                          {{ user.last_name }}
                        </td>
                        <td
                          class="px-6 py-4 whitespace-nowrap text-sm text-blue-900"
                        >
                          <a :href="'mailto:' + user.email">
                            {{ user.email }}
                          </a>
                        </td>
                        <td
                          class="px-6 py-4 whitespace-nowrap text-sm text-gray-500"
                        >
                          {{ user.country }}
                        </td>
                        <td
                          class="px-6 py-4 whitespace-nowrap text-sm text-gray-500"
                        >
                          {{ user.modified }}
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm">
                          <span
                            class="px-3 py-1 inline-flex text-xs leading-5 font-semibold rounded-full"
                            :class="
                              user.status
                                ? 'bg-green-100 text-green-800'
                                : 'bg-red-100 text-red-800'
                            "
                          >
                            {{ user.status ? "Online" : "Offline" }}
                          </span>
                        </td>
                        <td
                          class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium"
                        >
                          <button
                            @click="enableEditing(index)"
                            v-if="!hideTools"
                            type="button"
                            class="inline-flex items-center px-3 py-1 border border-transparent text-sm font-medium rounded-full shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
                          >
                            Edit user
                          </button>
                        </td>
                        <td
                          class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium"
                        >
                          <button
                            @click="removeUser(index)"
                            v-if="!hideTools"
                            type="button"
                            class="inline-flex items-center px-3 py-1 border border-transparent text-sm font-medium rounded-full shadow-sm text-white bg-red-600 hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-600"
                          >
                            Dismiss
                          </button>
                        </td>
                      </tr>
                      <tr v-if="usersBase[index].editable">
                        <td
                          class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900"
                        >
                          {{ user.id }}
                        </td>
                        <td
                          class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900"
                        >
                          <input
                            v-model="editableUserName"
                            class="bg-white-100 w-full h-10 p-2 rounded-xl bg-gray-100 text-gray-900 shadow-inner focus:ring-0 focus:outline-none"
                          />
                        </td>
                        <td
                          class="px-6 py-4 whitespace-nowrap text-sm text-gray-500"
                        >
                          <input
                            v-model="editableUserLastName"
                            class="bg-white-100 h-10 p-1 rounded-xl bg-gray-100 text-gray-900 shadow-inner focus:ring-0 focus:outline-none"
                          />
                        </td>
                        <td
                          class="px-6 py-4 whitespace-nowrap text-sm text-gray-500"
                        >
                          <input
                            v-model="editableUserEmail"
                            class="bg-white-100 h-10 p-1 rounded-xl bg-gray-100 text-gray-900 shadow-inner focus:ring-0 focus:outline-none"
                          />
                        </td>
                        <td
                          class="px-6 py-4 whitespace-nowrap text-sm text-gray-500"
                        >
                          <input
                            v-model="editableUserCountry"
                            class="bg-white-100 h-10 p-1 rounded-xl bg-gray-100 text-gray-900 shadow-inner focus:ring-0 focus:outline-none"
                          />
                        </td>
                        <td
                          class="px-6 py-4 whitespace-nowrap text-sm text-gray-500"
                        >
                          {{ user.modified }}
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm">
                          <span
                            class="px-3 py-1 inline-flex text-xs leading-5 font-semibold rounded-full"
                            :class="
                              user.status
                                ? 'bg-green-100 text-green-800'
                                : 'bg-red-100 text-red-800'
                            "
                          >
                            {{ user.status ? "Online" : "Offline" }}
                          </span>
                        </td>
                        <td
                          class="px-6 py-4whitespace-nowrap text-right text-sm font-medium"
                        >
                          <button
                            type="button"
                            @click="saveEdit(index)"
                            class="inline-flex items-center px-3 py-1 border border-transparent text-sm font-medium rounded-full shadow-sm text-white bg-green-600 hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-600"
                          >
                            Save
                          </button>
                        </td>
                        <td>
                          <button
                            type="button"
                            @click="disableEditing(index)"
                            class="inline-flex items-center px-3 py-1 border border-transparent text-sm font-medium rounded-full shadow-sm text-white bg-red-600 hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-600"
                          >
                            Disable
                          </button>
                        </td>
                      </tr>
                    </tbody>
                  </table>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      usersBase: [],
      idsBase: [],
      title: "Users in Parkopedia",
      show: false,
      hide: true,
      editable: "",
      sortBy: "name",
      sortDirection: "asc",
      editableUserName: "",
      editableUserLastName: "",
      editableUserEmail: "",
      editableUserCountry: "",
      hideTools: false,
    };
  },
  mounted() {
    axios.get("http://localhost:3000/users").then((response) => {
      this.usersBase = response.data;
    });
  },
  methods: {
    sort(s) {
      if (s === this.sortBy) {
        this.sortDirection = this.sortDirection === "asc" ? "desc" : "asc";
      }
      this.sortBy = s;
      return this.usersBase.sort((p1, p2) => {
        let modifier = 1;
        if (this.sortDirection === "desc") modifier = -1;
        if (p1[this.sortBy] < p2[this.sortBy]) return -1 * modifier;
        if (p1[this.sortBy] > p2[this.sortBy]) return 1 * modifier;
        return 0;
      });
    },
    zerofill(i) {
      return (i < 10 ? "0" : "") + i;
    },
    currentDateTime() {
      const current = new Date();
      const date =
        current.getFullYear() +
        "-" +
        this.zerofill(current.getMonth() + 1) +
        "-" +
        this.zerofill(current.getDate());
      const dateTime = date;
      return dateTime;
    },
    disableEditing(index) {
      this.usersBase[index].editable = false;
      this.hideTools = false;
      this.editableUserName = "";
      this.editableUserLastName = "";
      this.editableUserEmail = "";
      this.editableUserCountry = "";
    },
    saveEdit(index) {
      this.usersBase[index]["first_name"] = this.editableUserName;
      this.usersBase[index]["last_name"] = this.editableUserLastName;
      this.usersBase[index]["email"] = this.editableUserEmail;
      this.usersBase[index]["country"] = this.editableUserCountry;
      this.usersBase[index]["modified"] = this.currentDateTime();
      this.disableEditing(index);
    },
    enableEditing(index) {
      this.hideTools = true;
      this.usersBase[index].editable = true;
      this.editableUserName = this.usersBase[index]["first_name"];
      this.editableUserLastName = this.usersBase[index]["last_name"];
      this.editableUserEmail = this.usersBase[index]["email"];
      this.editableUserCountry = this.usersBase[index]["country"];
    },
    creatUniqueId() {
      this.maxId  = this.usersBase.reduce((prev, current) => (+prev.id > +current.id) ? prev : current)
      return this.maxId["id"] + 1;
    },
    addNewUser(newUserName, newUserLastName, newUserEmail, newUserCountry) {
      this.usersBase.unshift({
        id: this.creatUniqueId(),
        first_name: newUserName,
        last_name: newUserLastName,
        email: newUserEmail,
        country: newUserCountry,
        modified: this.currentDateTime(),
      });
      this.hideUserAddTool();
    },
    showUserAddTool() {
      this.show = true;
      this.hide = false;
      this.hideTools = true;
    },
    hideUserAddTool() {
      this.show = false;
      this.hideTools = false;
      this.hide = true;
      this.newUserName = "";
      this.newUserLastName = "";
      this.newUserEmail = "";
      this.newUserCountry = "";
    },
    closeModal() {
      this.show = false;
    },
    removeUser(index) {
      this.usersBase.splice(index, 1);
    },
  },
  computed: {},
};
</script>

<style>
.pointer {
  cursor: pointer;
}
.asc:after {
  content: "\25B2";
}

.desc:after {
  content: "\25BC";
}
</style>
