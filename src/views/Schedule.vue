<template>
    <BigAdvertising />
    <div class="wrapper container">
        <Sidebar />
        <section class="schedule">
            <div class="schedule-content">
                <h2 class="schedule-title">Расписание на неделю</h2>
                <span class="schedule-text">СПО - 1- 20</span>
                <div class="schedule-wrapper">
                    <table>
                        <thead>
                            <tr v-for="day in days" :key="day">
                                <td>{{ day }}</td>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td class="schedule-another" v-for="time in times" :key="time.id">
                                    <span>{{ time.start }}</span>
                                    <span>{{ time.end }}</span>
                                </td>
                            </tr>
                            <tr v-for="items in mvp" :key="items">
                                <td v-for="item in items" :key="item.id">
                                    <div class="schedule-block">
                                        <p class="schedule-name">{{ item?.discipline?.urok?.title }}</p>
                                        <span class="schedule-time">
                                            <svg width="10" height="10" viewBox="0 0 10 10" fill="none"
                                                xmlns="http://www.w3.org/2000/svg">
                                                <path
                                                    d="M5.25714 0.748535C2.81222 0.748535 0.831299 2.72946 0.831299 5.17438C0.831299 7.6193 2.81222 9.60022 5.25714 9.60022C7.70206 9.60022 9.68298 7.6193 9.68298 5.17438C9.68298 2.72946 7.70206 0.748535 5.25714 0.748535ZM9.1119 5.17438C9.1119 7.29271 7.39689 9.02914 5.25714 9.02914C3.1388 9.02914 1.40237 7.31413 1.40237 5.17438C1.40237 3.05604 3.11739 1.31961 5.25714 1.31961C7.37547 1.31961 9.1119 3.03462 9.1119 5.17438ZM6.45461 6.75019L5.00551 5.69727C4.95019 5.65622 4.91806 5.59197 4.91806 5.52416V2.67592C4.91806 2.55813 5.01443 2.46176 5.13222 2.46176H5.38206C5.49985 2.46176 5.59622 2.55813 5.59622 2.67592V5.28681L6.85437 6.20231C6.95074 6.27191 6.97037 6.40576 6.90077 6.50213L6.75443 6.70379C6.68483 6.79837 6.55098 6.81979 6.45461 6.75019Z"
                                                    fill="#1EA9B9" />
                                            </svg>
                                            {{ item?.time }}
                                        </span>
                                    </div>
                                </td>
                            </tr>

                        </tbody>
                    </table>
                </div>
            </div>
        </section>
        <Calendar />
    </div>
</template>

<script setup>
import BigAdvertising from '../components/advertising/BigAdvertising.vue';
import Sidebar from '../layout/Sidebar.vue';
import Calendar from '../layout/Calendar.vue';
import { onMounted, ref, watch } from 'vue';
import { useStore } from 'vuex';
import { useRoute, useRouter } from 'vue-router';
const times = ref([
    {
        id: 0,
        start: "09:00",
        end: "10:00"
    },
    {
        id: 1,
        start: "11:00",
        end: "12:00"
    },
    {
        id: 2,
        start: "13:00",
        end: "14:00"
    },
    {
        id: 3,
        start: "15:00",
        end: "16:00"
    },
    {
        id: 4,
        start: "17:00",
        end: "18:00"
    },
])
const days = ref(["неделя", "Пн", "Вт", "Ср", "Чт", "Пт", "Сб",])
const store = useStore();
const mvp = ref([])
const router = useRouter()


const token = localStorage.getItem("access");

const localToken = ref('');

watch(() => router.currentRoute, () => {
    localToken.value = token
})

const getChedule = async () => {
    const token = localStorage.getItem("access");
    const url = store.state.URL + 'api/v1/schedule/'
    const bearer = `Bearer ${token}`
    console.log(bearer)
    fetch(url, {
        headers: {
            Authorization: `Bearer ${localToken}`,
        },
    })
        .then((response) => response.json())
        .then((data) => {
            const days = Object.keys(data);
            days.forEach(day => {
                mvp.value.push(data[day]);
            });
        })
        .catch((error) => {
            throw new Error(error.message)
        });
}

onMounted(async () => {
    await getChedule()
});
</script>

<style lang="scss">
.schedule {
    background: #FFFFFF;
    border-radius: 30px;
    font-family: 'Montserrat';
    padding: 28px 32px 0 32px;
    box-sizing: border-box;
    width: 580px;

    &-title {
        font-weight: 700;
        font-size: 18.222px;
        color: #000000;
        margin-bottom: 31px;
    }

    &-text {
        font-weight: 600;
        font-size: 11.2135px;
        color: #000000;
    }

    &-wrapper {
        overflow: auto;
        width: 500px;
    }

    table {
        margin-top: 60px;
        background-image: linear-gradient(0deg, transparent 99%, #dcdcdc 10%);
        background-size: 10px 32px;
        background-color: #ffffff;

        thead {
            padding: 8.41px 17.52px 7.71px 32px;
            background: #ffffff;
            display: flex;
            align-items: center;
            // gap: 102px;
            margin-bottom: 10px;
            align-items: center;

            tr {

                // margin-left: ;
                &:not(:first-child) {
                    margin-left: 100px;
                }

                &:nth-child(2) {
                    margin-left: 80px;
                }
            }
        }

        tbody {
            display: flex;
            gap: 30px;
            align-items: baseline;

            tr {
                display: flex;
                flex-direction: column;
                justify-content: space-between;
                gap: 4px;

                &:first-child {
                    display: flex;
                    flex-direction: column;
                    gap: 5px;
                    margin-right: 20px;
                }

                .schedule-another {
                    width: 50px;
                    display: flex;
                    flex-direction: column;
                    align-items: center;
                    padding: 9.41px 17.52px 2.71px 32px;
                    gap: 10px;
                    background: #ffffff;

                    span {
                        text-align: center;
                    }
                }

            }
        }

    }

    &-name {
        font-weight: 500;
        font-size: 8.41015px;
        color: #1EA9B9;
    }

    &-time {
        display: flex;
        align-items: center;
        font-weight: 400;
        font-size: 7.00846px;
        color: #1EA9B9;
        gap: 4.33px;
    }

    &-block {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: start;
        width: 96px;
        height: 59px;
        background: #E9EFFF;
        border-radius: 4.20507px;
        border-left: 3.65px solid #1EA9B9;
        padding: 5.67px 5px 3.78px 10px;
        box-sizing: border-box;
    }
}
</style>