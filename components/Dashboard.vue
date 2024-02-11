<template>
  <div class="w-full">
    <h1 class="text-3xl font-extrabold" style="font-weight:bolder;">
      Welcome back, Administrator
    </h1>
    <p class="font-light text-sm">
      Track, manage and forecast your platform information here
    </p>
    <div class="flex mt-7 gap-7 mb-5">
      <UCard class="h-36 w-96">
        <div class="flex justify-between">
          <div>
            <h1 class="font-bold text-sm">Revenue in Percentage</h1>
            <h1 class="text-xs font-bold mt-10 text-green-400">
              40% vs last month
            </h1>
          </div>
          <div>
            <Icon
              name="carbon:chart-line-smooth"
              color="green"
              size="100"
              class="ms-2"
            />
          </div>
        </div>
      </UCard>
      <UCard class="h-36 w-96">
        <div class="flex justify-between">
          <div>
            <h1 class="font-bold text-sm">Total Order</h1>
            <h1 class="text-2xl font-bold mt-10">
              {{companies.length}}&nbsp;Order
            </h1>
          </div>
          <div>
            <Icon
              name="fluent-emoji-flat:ledger"
              color="white"
              size="40"
              class="ms-2"
            />
          </div>
        </div>
      </UCard>
      <UCard class="h-36 w-96">
        <div class="flex justify-between">
          <div>
            <h1 class="font-bold text-sm">Pending Customer</h1>
            <h1 class="text-2xl font-bold mt-10">20 Customer</h1>
          </div>
          <div>
            <Icon
              name="flat-color-icons:overtime"
              color="white"
              size="40"
              class="ms-2"
            />
          </div>
        </div>
      </UCard>
    </div>
    <div class="flex justify-end mb-5">
      <UInput
        v-model="searchQuery"
        class="w-1/4"
        icon="i-heroicons-magnifying-glass-20-solid"
        size="md"
        color="white"
        :trailing="false"
        placeholder="Search"
      />
    </div>
    <UCard>
      <div>
        <table>
          <thead>
            <tr>
              <th class="me-36">Company</th>
              <th class="me-36">License Use</th>
              <th>Status</th>
              <th>Users</th>
              <th>About</th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="company in companies"
              :key="company.id"
              class="gap-10 mb-5 text-sm"
            >
              <td class="flex items-center px-4">
                <UCheckbox class="me-3" :model-value="false" />
                <div>
                  <img
                    :src="company.avatar"
                    alt="Company Avatar"
                    style="width: 30px; height: 30px; border-radius:100% ; margin-right: 4px;"
                  />
                </div>
                <div>
                  {{ company.name }}
                </div>
              </td>
              <td class="items-center px-4">
                <UProgress :value="calculateProgress(company.user.length)" />
              </td>
              <td class="items-center ml-30  px-4">
                {{ company.status ? 'Active' : 'Inactive' }}
              </td>
              <td class="items-center ml-20  px-4">
                <img
                  :src="company.user"
                  alt="User Avatar"
                  style="width: 30px; height: 30px; border-radius:100%"
                />
              </td>
              <td class="flex-row  ml-44 items-center px-4">
                {{ company.about }}
              </td>
              <td>
                <div class="ml-10">
                  <button>
                    <Icon name="ph:trash" color="grey" size="20" />
                  </button>
                  <button class="ml-3">
                    <Icon name="lucide:pen" color="grey" size="20" />
                  </button>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </UCard>
    <UPagination :total="totalPages" v-model:page="currentPage" />
  </div>
</template>

<script setup>
const { data: companies } = await useFetch('https://65c75151e7c384aada6e62a7.mockapi.io/api/v1/company')

const calculateProgress = (length) => {
  return Math.min(Math.max((length / 100) * 100, 0), 100);
};
const currentPage = ref(1);
const perPage = 5;
const searchQuery = ref('');

// Menghitung total halaman
const totalPages = computed(() => Math.ceil(filteredCompanies.length / perPage));

// Fungsi untuk menyaring data berdasarkan pencarian
const filteredCompanies = computed(() => {
  if (!searchQuery.value) {
    return companies;
  }
  const query = searchQuery.value.toLowerCase();
  return companies.filter(company =>
    company.name.toLowerCase().includes(query) ||
    company.about.toLowerCase().includes(query)
  );
});
</script>

<style scoped>
@media (max-width: 1024px) {
  .w-full {
    padding: 0 20px;
  }
}

@media (max-width: 800px) {
  .w-full {
    padding: 0 10px;
  }
}

@media (max-width: 500px) {
  .w-full {
    padding: 0 5px;
  }
}
</style>
