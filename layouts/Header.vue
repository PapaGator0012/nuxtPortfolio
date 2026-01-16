

<script setup>

// menu sticky 
const isSticky = ref(false);
const handleSticky = () => {
  if (window.scrollY > 80) {
    isSticky.value = true;
  } else {
    isSticky.value = false;
  }
};

onMounted(() => {
  window.addEventListener('scroll', handleSticky);
});
onUnmounted(() => {
  window.removeEventListener('scroll', handleSticky);
});


const openMenu = ref(false)
const toggleMenu = () => {
  openMenu.value = !openMenu.value
}


import menu_data from "../data/menu_data"

</script>


<template>

<div>
    <header :class="`main-header ${isSticky ? 'fixed-header' : ''}`">
        <div class="header-upper">
            <div class="container">
                <div class="header-inner">
                    <div class="row align-items-center">
                        <div class="col-xl-2 col-lg-2 col-md-6 col-6 col-sm-3">
                            <div class="logo-area">
                                <div class="logo">
                                    <NuxtLink to="/"><img src="assets/images/logo.png" alt=""></NuxtLink>
                                </div>
                            </div>
                        </div>
                        <div class="col-xl-10 col-lg-10 col-md-6 col-6 col-sm-9">
                          <div class="main-menu d-none d-lg-block">
                            <nav id="mobile-menu">
                                <ul>
                                    <!-- Manually add the "Contact" button here -->
                                    <li>
                                        <NuxtLink to="/contact" class="linkstyle">Contact MD</NuxtLink>
                                    </li>
                                </ul>
                            </nav>
                        </div>

                            <div class="side-menu-icon d-lg-none text-end">
                                <a style="cursor: pointer;" 
                                @click="toggleMenu"
                                class="info-toggle-btn f-right sidebar-toggle-btn"><i class="fal fa-bars"></i></a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <CommonSidebar :toggleMenu="toggleMenu" :openMenu="openMenu"  />
</div>
  

</template>

