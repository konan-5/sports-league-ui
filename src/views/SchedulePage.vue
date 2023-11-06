<script setup>
import LeagueService from '@/services/LeagueService';
import Header from '@/components/Header.vue';
import { FLAGAPI_URL } from '@/utils/constants'
</script>
<template>
    <Header></Header>

    <table class="schedule">
        <thead>
            <tr>
                <th>Date/Time</th>
                <th>Stadium</th>
                <th>Home Team</th>
                <th></th>
                <th>Away Team</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(match, index) in  matches " :key="index">
                <!-- <td class="date-time">{{ match.matchDate }}</td> -->
                <td>
                    <p>{{ formatDate(match.matchDate) }}</p>
                    <p>{{ formatTime(match.matchDate) }}</p>
                </td>
                <td>{{ match.stadium }}</td>
                <td>
                    <div class="home-team">
                        <p class="country-name">{{ match.homeTeam }}</p>
                        <img :src="FLAGAPI_URL + match.homeTeam + '.png'" class="country-flag" alt="Country Flag" />
                    </div>
                </td>
                <td>

                    <span>{{ match.homeTeamScore }}</span>
                    <span>:</span>
                    <span>{{ match.awayTeamScore }}</span>

                </td>
                <td>
                    <div class="away-team">
                        <img :src="FLAGAPI_URL + match.awayTeam + '.png'" class="country-flag" alt="Country Flag" />
                        <p class="country-name">{{ match.awayTeam }}</p>
                    </div>
                </td>
            </tr>
        </tbody>
    </table>
</template>
<script>
export default {
    data() {
        return {
            matches: [],
        };
    },
    methods: {
        formatDate(matchDate) {
            const date = new Date(matchDate);
            const day = date.getDate();
            const month = date.getMonth() + 1; // Months are zero-indexed
            const year = date.getFullYear();
            const formattedDate = `${day}.${month}.${year}`;
            return formattedDate;
        },
        formatTime(matchDate) {
            const date = new Date(matchDate);
            const hours = date.getHours();
            const minutes = date.getMinutes();
            const formattedTime = `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}`;
            return formattedTime;
        }
    },
    created() {
        const leagueService = new LeagueService();
        leagueService.fetchData()
            .then(() => {
                this.matches = leagueService.getMatches();
            })
            .catch((error) => {
                console.error('Error:', error)
            })

    }
}
</script>
<style>
table.schedule,
table.schedule tr,
table.schedule th,
table.schedule td {
    border-collapse: collapse;
}

table.schedule {
    width: 90%;
    font-family: sans-serif;
    margin-bottom: 10px;
    margin-left: auto;
    margin-right: auto;
}

table.schedule th {
    height: 40px;
    font-size: 12px;
    vertical-align: middle;
    background-color: #E4EDF2;
    padding: 0 18px;
}

table.schedule td {
    height: 70px;
    font-size: 14px;
    vertical-align: middle;
    padding: 0 18px;
}

table.schedule td img {
    width: 53px;
    height: 37px;
}

table.schedule td:first-child p {
    text-align: right;
}

table.schedule tr th:nth-child(1),
table.schedule tr td:nth-child(1) {
    width: 8%;
    padding-right: 50px;
}

table.schedule tr th:nth-child(2) {
    text-align: left;
}

table.schedule tr th:nth-child(3),
table.schedule tr td:nth-child(3) {
    width: 30%;
}

table.schedule tr th:nth-child(3) {
    text-align: right;
}

table.schedule tr th:nth-child(5) {
    text-align: left;
}

table.schedule tr th:nth-child(4),
table.schedule tr td:nth-child(4) {
    width: 5%;
    text-align: center;
}

table.schedule tr td:nth-child(3)>div {
    column-gap: 22px;
    display: flex;
    justify-content: flex-end;
    align-items: center;

}

table.schedule tr td:nth-child(5)>div {
    column-gap: 22px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
}

table.schedule tr th:nth-child(5),
table.schedule tr td:nth-child(5) {
    width: 30%;

}

table.schedule tr td:nth-child(3) *,
table.schedule tr td:nth-child(4) *,
table.schedule tr td:nth-child(5) * {
    font-weight: 700;
    font-size: 16px;
    color: #182C62;
}

table.schedule tr:nth-child(even) {
    background-color: #F6F7F7;
}

tr:not(:last-child) {
    border-bottom: 1px solid #E4EDF2;
}

@media only screen and (max-width: 750px) {

    table.schedule tr th:nth-child(2),
    table.schedule tr td:nth-child(2) {
        display: none;
    }

    table.schedule tr th:nth-child(1),
    table.schedule tr td:nth-child(1) {
        padding-right: 0;
    }
}

@media only screen and (max-width: 500px) {

    table.schedule tr th:nth-child(1),
    table.schedule tr td:nth-child(1) {
        display: none;
    }
}
</style>