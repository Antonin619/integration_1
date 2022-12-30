<template>
    <section class="mobile_menu shadow-lg">
            <a href="/dashboard" ><img class="menu_logo" src="~/assets/logo.png" alt="logo"></a>
            <div class="right-side">
                <button class="notifications-button" @click="toggleNotificationsMenu()">
                    <client-only><font-awesome-icon class="notifications" icon="fa-solid fa-bell" /></client-only>
                </button>
                    <div @click="areNotificationsOpen=false" :class="[areNotificationsOpen?'notification-click-background' : 'notification-click-background hidden-notifications']"></div>
                    <div :class="[areNotificationsOpen?'notifications-center' : 'notifications-center hidden-notifications']">
                        <h5 class="notification-title">Notifications</h5>
                        <p class="read-all-button" @click="readAll()">Mark all as read</p>
                        <Notification v-for="notification in notifications" :key="notification.id" :id="notification.id" :title="notification.title" :description="notification.description" :date="notification.date" :read="notification.read"/>
                        <p class="no-notifications" v-if="notifications.length == 0">Aucune notification...</p>
                    </div>
                
                <button class="burger-button" @click="toggleMenu()"><client-only><font-awesome-icon class="burger" icon="fa-solid fa-bars" /></client-only></button>
            </div>
            <div @click="isOpen=false" :class="[isOpen?'menu-background-blur menu-background-blur-open' : 'menu-background-blur']"></div>
            <nav :class="[isOpen?'menu shadow-2xl menu-open' : 'menu']">
                <div class="menu_header">
                    <img class="menu_logo" src="~/assets/logo.png" alt="logo">
                    <button class="burger-button" @click="toggleMenu()"><client-only><font-awesome-icon class="burger-cross" icon="fa-solid fa-times" /></client-only></button>
                </div>
                <ul class="menu_list">
                    <li :class="[route.name=='dashboard'? 'menu_item active-link' : 'menu_item']"><a @click="toggleMenu()" href="/dashboard"><client-only><font-awesome-icon class="pr-4" icon="fa-solid fa-house" /></client-only>Dashboard</a></li>
                    <li :class="[route.name=='features'? 'menu_item active-link' : 'menu_item']"><a @click="toggleMenu()" href="/features"><client-only><font-awesome-icon class="pr-4" icon="fa-solid fa-border-all" /></client-only>Features</a></li>
                    <li :class="[route.name=='collaborators'? 'menu_item active-link' : 'menu_item']"><a @click="toggleMenu()" href="/collaborators"><client-only><font-awesome-icon class="pr-4" icon="fa-solid fa-user-group" /></client-only>Collaborators</a></li>
                    <li :class="[route.name=='calculator'? 'menu_item active-link' : 'menu_item']"><a @click="toggleMenu()" href="#"><client-only><font-awesome-icon class="pr-4" icon="fa-solid fa-calculator" /></client-only>Calculator</a></li>
                </ul>

                <div class="menu_footer">
                    <div class="user-utils">
                        <button class="account-button">
                            <img class="account-picture" src="https://i.pravatar.cc/300" alt="profil">
                        </button>
                        <button class="logout-button">
                            <client-only><font-awesome-icon class="logout-icon" icon="fa-solid fa-sign-out-alt" /></client-only>
                        </button>
                    </div>
                    <button class="parameters"><client-only><font-awesome-icon class="logout-icon" icon="fa-solid fa-gear" /></client-only></button>
                </div>
            </nav>
    </section>
    <div class="empty-container"></div>
    <slot></slot>
</template>

<script lang="ts" setup>
const isOpen = ref(false);
const areNotificationsOpen = ref(false);

function toggleMenu() {
    isOpen.value = !isOpen.value;
}

function toggleNotificationsMenu() {
    areNotificationsOpen.value = !areNotificationsOpen.value;
    console.log('coucou', areNotificationsOpen.value)
}

const route = useRoute()

const notifications = ref([
    {
        id: 1,
        title: "Happy new year !",
        description: "Our team wish you the best for this new year !",
        date: "2023-01-01",
        read: false
    },
    {
        id: 2,
        title: "New 2023 update incoming !",
        description: "New features will be added to the platform for the new year !",
        date: "2022-30-12",
        read: false
    },
    {
        id: 3,
        title: "Merry Christmas !",
        description: "Our team wish you a merry christmas !",
        date: "2022-25-12",
        read: true
    }
]);

function readAll() {
    for (let i = 0; i < notifications.value.length; i++) {
        notifications.value[i].read = true;
        notifications.value[i].description = 'coucou';
    }
}

</script>

<style lang="scss" scoped>
.menu {
    backdrop-filter: blur(1px);
    -webkit-backdrop-filter: blur(1px);
    background-color: rgba(255, 255, 255, 0.712);
    transform: translateX(100%);
    transition: transform 0.3s ease-in-out;
    position: fixed;
    top: 0;
    right: 0;
    width: 80vw;
    height: 100vh;
    padding: 1rem;
    padding-right: 2rem;
    z-index: 10;

    border-left: 5px solid white;

    .menu_header {
        display: flex;
        justify-content: space-between;
        

        .burger-cross {
            min-height: 40px;
            color: rgb(170, 170, 170);
        }
    }

    .menu_list {
        display: flex;
        flex-direction: column;
        gap: 1rem;
        margin-top: 2rem;
        text-align: left;

        .menu_item {
            font-size: 1rem;
            font-weight: 400;
            color: black;

            a {
                .pr-4 {
                    width: 30px;
                }
            }
        }

        .active-link {
            font-weight: 700;
            color: rgb(71, 0, 185);
        }
    }

    .menu_footer {
        display: flex;
        position: fixed;
        bottom: 11vh;
        font-size: 1.5rem;
        width: 100%;
        justify-content: space-between;
        padding-right: 3rem;
        color: rgb(83, 83, 83);

        .user-utils {
            display: flex;
            gap: 10px;
            justify-content: space-between;

            .account-button {
                overflow: hidden;
                border-radius: 50%;
                width: 5rem;
                height: 5rem;
            }
        }
    }
}

.menu-open {
    transform: translateX(0);
}

.menu-background-blur {
    display: none;
    width: 100vw;
    height: 100vh;
    content: '';
    backdrop-filter: brightness(0.8) blur(10px);
    -webkit-backdrop-filter: brightness(0.8) blur(20px);
    opacity: 0;
    z-index: -1;
    position: fixed;
    top: 0;
    right: 0;
    transition: all 0.3s;
    
}

.menu-background-blur-open {
    display: block;
    opacity: 1;
    z-index: 9;
    
}

.empty-container {
    height: 10vh;
}

.mobile_menu {
    max-height: 10vh;
    width: 100%;
    display: flex;
    justify-content: space-between;
    padding: 1rem;
    padding-left: 1.5rem;
    padding-right: 1.5rem;
    position: fixed;
    backdrop-filter: blur(6px);
    z-index: 1000;

    .menu_logo {
        max-height: 30px;
    }

    .right-side {
        display: flex;
        gap: 2rem;

        button {

            background-color: transparent;
            border: none;

            .burger {
                min-height: 30px;
                color: rgb(170, 170, 170);
            } 

            .notifications {
                min-height: 20px;
                color: rgb(170, 170, 170);

            }
        }
    }
    
}



.notifications-center {
    position:absolute;
    width: 50vw;
    top: 3rem;
    right: 1rem;
    background-color: rgb(255, 255, 255);
    display: flex;
    flex-direction: column;
    border-radius: 0.5rem;
    text-align: left;
    padding: 1rem;
    box-shadow: 0 0 10px 0 rgba(82, 74, 74, 0.2);
    

    h5 {
        color: black;
        padding-bottom: 0.5rem;
        border-bottom: 1px solid rgb(71, 0, 185);
        
    }

    .no-notifications {
        padding: 1rem 0;
        opacity: 0.5;
    }

    .read-all-button {
        color: rgb(71, 0, 185);
        transform: uppercase;
        text-decoration: underline;
        font-size: 10px;
        margin-top: 0.5rem;
        margin-bottom: 1rem;
    }
}

.hidden-notifications {
    display: none !important;
}

.notification-click-background {
    position: fixed;
    top: 0;
    left: 0;
    background-color: transparent;
    height: 100vh;
    width: 100vw;
}
</style>