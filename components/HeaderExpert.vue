<template>
    <div>
        <div class="d-flex flex-row justify-content-between align-items-center header-expert">
            <div class="pr-5 px18 fw500 blueGrey">

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
            <div class="px-3 gradient d-flex align-items-center">
                <LazySectionMultimediaTests />
            </div>
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
        height: 92px;
        background-color: #1c3668;

        .gradient {
            height: 100%;
            background-image: linear-gradient(80deg, #254176 11%, #1c3668 95%);
        }
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
        overflow-x: hidden;
        box-shadow: -25px 13px 0 #1c3668, 
                    0px 10px 0 #1c3668, 
                    0px 12px 0 white;
    }
</style>