<template>
    <div class="d-flex flex-row align-items-center justify-content-between header-expert">
        <div class="col-12 col-lg-6 p-0 m-0 align-items-center">
            <div class="d-flex flex-row align-items-center pr-2 pr-lg-5 px18 fw500 blueGrey header-expert-nav">

                <NuxtLink to="/">
                    {{messages.nav.about.ar}}
                    {{doctor.firstName}}
                </NuxtLink>

                <NuxtLink to="/expert-store">
                    {{messages.nav.store.ar}}
                </NuxtLink>

                <NuxtLink to="/expert-broadcast">
                    {{messages.nav.broadcast.ar}}
                </NuxtLink>

                <NuxtLink to="/expert-courses">
                    {{messages.nav.courses.ar}}
                </NuxtLink>

                <NuxtLink to="/expert-reserve">
                    {{messages.nav.reserve.ar}}
                    (
                        {{doctor.reservePrice}}
                        {{messages.currency.ar}}
                    )
                </NuxtLink>

            </div>

        </div>
        
        
        <div class="col-12 col-lg-6 p-0 d-none d-lg-block">
            <LazySectionMultimediaTests />
        </div>
    </div>
</template>

<script>
    import * as data  from "../assets/data/db.json";

    export default {
        setup() {

            return {
                messages: data.messages,
                doctor: data.doctor
            }
        }
        
    }
</script>

<style lang="scss" scoped>
    .header-expert {
        background-color: #1c3668;

        .header-expert-nav{
            max-width: 100vw;
            overflow-x: scroll;
            overflow-y: visible;
            white-space: nowrap;
            height: 92px;
        }
    }

    .header-expert-nav::-webkit-scrollbar {
        display: none;
    }

    a {
        margin-left: 40px;
        color: #8191b2 !important;
    }

    a:hover {
        text-decoration: none !important;
    }

    .nuxt-link-exact-active {
        color: white !important;
        // overflow-x: hidden;
        box-shadow: -25px 13px 0 #1c3668, 
                    0px 10px 0 #1c3668, 
                    0px 12px 0 white;
    }
</style>