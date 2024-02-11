<template>
  <div
    class="sidebar bg-slate-800 w-64 p-1 h-screen overflow-y-auto fixed-top sticky"
  >
    <h1 class="text-white font-bold text-xl">Visa Indonesia</h1>
    <ul>
      <li :class="{ active: isActive('/') }">
        <nuxt-link to="/">
          <a
            href="Dashboard.vue"
            class="block text-white  py-2 px-3 text-sm hover:bg-slate-700 rounded-lg"
          >
            <Icon name="carbon:home" color="white" size="20" class="mr-1" />
            Dashboard</a
          >
        </nuxt-link>
      </li>
      <li>
        <a
          href="#"
          class="block text-white  py-2 px-3 text-sm hover:bg-slate-700 rounded-lg"
        >
          <Icon name="gala:layer" color="white" class="mr-1" size="20" />
          Service</a
        >
      </li>
      <li>
        <a
          href="#"
          class="block text-white  py-2 px-3 text-sm hover:bg-slate-700 rounded-lg"
        >
          <Icon
            name="carbon:open-panel-bottom"
            color="white"
            class="mr-2"
            size="20"
          />Order</a
        >
      </li>
      <li>
        <a
          href="#"
          class="block text-white  py-2 px-3 text-sm hover:bg-slate-700 rounded-lg"
        >
          <Icon
            name="octicon:people-24"
            color="white"
            class="mr-2"
            size="20"
          />Customer</a
        >
      </li>
      <li>
        <a
          href="#"
          class="block text-white  py-2 px-3 text-sm hover:bg-slate-700 rounded-lg"
        >
          <Icon
            name="ph:suitcase"
            color="white"
            class="mr-2"
            size="20"
          />Customer Identity</a
        >
      </li>
      <li>
        <a
          href="#"
          class="block text-white  py-2 px-3 text-sm hover:bg-slate-700 rounded-lg"
        >
          <Icon
            name="ic:outline-local-offer"
            color="white"
            class="mr-2"
            size="20"
          />Promo Code</a
        >
      </li>
      <li>
        <a
          href="#"
          class="block text-white  py-2 px-3 text-sm hover:bg-slate-700 rounded-lg"
        >
          <Icon name="iconoir:user" color="white" class="mr-2" size="20" />Admin
          User</a
        >
      </li>
    </ul>
    <div class="mt-80 -ml-1" style="position:fixed">
      <hr class="w-60" />
      <div class="mt-auto flex">
        <div class="flex items-center justify-center mt-6 ">
          <UAvatar
            src="https://avatars.githubusercontent.com/u/739984?v=4"
            alt="Avatar"
            class="mr-3 "
          />
          <div class="text-white text-sm ">
            <p>Administrator</p>
            <p class="font-extralight">admin@spdigital.com</p>
          </div>
          <button>
            <Icon
              name="iconamoon:exit-light"
              color="white"
              size="25"
              class="ms-2 hover:bg-slate-700 rounded-lg"
            />
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SidebarMenu',
  methods: {
    isActive(route) {
      return this.$route.path === route;
    }
  }
}
</script>
<style scoped>
.sidebar {
  position: relative;
}

.active {
  background-color: #485264;
  border-radius: 5px;
}

@media (max-width: 1024px) {
  .sidebar {
    width: 50%;
  }
}

@media (max-width: 800px) {
  .sidebar {
    width: 70%;
  }
}

@media (max-width: 500px) {
  .sidebar {
    width: 100%;
  }
}
</style>
