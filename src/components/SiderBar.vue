<script >
import { RouterLink } from 'vue-router'

export default {
    name: 'SiderBar',
    components: {
        
    },
    data() {
        return{
        tabs: [
            {icon: 'fas fa-home', title: 'Home', id:'home', to:'/'},
            {icon: 'fas fa-hashtag', title: 'Explore', id: 'explore', to:'/about'},
            {icon: 'far fa-bell', title: 'Notifications', id: 'notifications', to:'/'},
            {icon: 'far fa-envelope', title: 'Messages', id: 'messages', to:'/'},
            {icon: 'far fa-bookmark', title: 'Bookmarks', id: 'bookmarks', to:'/'},
            {icon: 'fas fa-clipboard-list', title: 'Lists', id: 'lists', to:'/'},
            {icon: 'far fa-user', title: 'Profile', id: 'profile', to:'/'},
            {icon: 'fas fa-ellipsis-h', title: 'More', id: 'more', to:'/'}
        ],
        id: 'home',
        dropdown: false,
        }
    }
}
    
</script>

<template>
    <div class="sidebar lg:w-1/5 border-r boder-lighter px-2 lg:px-6 py-2 flex flex-col justify-between">
        <div>
            <button class="h-12 w-12 hover:bg-lightblue rounded-full text-3xl text-blue">
                <i class="fab fa-twitter"></i>
            </button>

            <div>
                <RouterLink :to="`${tab.to}`" @click="id = tab.id" :class=" `focus:outline-none flex hover:text-blue items-center py-2 px-4 hover:bg-lightblue rounded-full mr-auto mb-3 ${ id === tab.id ? 'text-blue' : ''}` " v-for="tab in tabs" v-bind:key="tab.id" >
                <i :class=" `${tab.icon} text-2xl mr-4 text-left` ">  </i>
                <p class="text-lg font-semibold text-left hidden lg:block">{{ tab.title }}</p>
                </RouterLink>
                <!-- <RouterLink to="/about">About</RouterLink> -->
            </div>

            <button class="text-white bg-blue rounded-full font-semibold focus:outline-none w-12 h-12 lg:h-auto lg:w-full p-3 hover:bg-darkblue">
                <p class="hidden lg:block">Tweet</p>
                <i class="fas fa-plus lg:hidden"></i>

            </button>
        </div>
        <div class="lg:w-full relative">
            <button @click="dropdown = true" class="flex items-center w-full hover:bg-lightblue rounded-full p-2 focus:outline-none" >
                <img src="profile-1.jpg" alt="Profile" class="w-10 h-10 rounded-full border border-lighter"/>
                <div class="hidden lg:block ml-4">
                    <p class="text-sm font-bold leading-tight">Japdz</p>
                    <p class="text-sm leading-tight">@japdz</p>
                </div>
                <i class="hidden lg:block fas fa-angle-down ml-auto text-lg"></i>
            </button>
            <div v-if="dropdown === true" class="absolute bottom-0 left-0 w-64 rounded-lg shadow-md border-lightest bg-white mb-16 ">
                <button @click="dropdown = false" class="flex items-center w-full hover:bg-lightblue rounded-lg p-3 focus:outline-none " >
                    <img src="profile-1.jpg" alt="Profile" class="w-10 h-10 rounded-full border border-lighter"/>
                    <div class="ml-4">
                        <p class="text-sm font-bold leading-tight">Japdz</p>
                    <p class="text-sm leading-tight">@japdz</p>
                    </div>
                    <i class="fas fa-check ml-auto text-blue"></i>
                </button>
                <button @click="dropdown = false" class="w-full text-left hover:bg-lightest border-t border-lighter p-3 test-sm focus:outline-none">
                    Add an existing account
                </button>
                <button @click="dropdown = false" class="w-full text-left hover:bg-lightest border-t border-lighter p-3 test-sm focus:outline-none">
                    Log out @SaaSyEth
                </button>
            </div>
        </div>
    </div>
</template>

<style scoped>

</style>