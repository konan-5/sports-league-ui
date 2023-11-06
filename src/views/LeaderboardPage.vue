<script setup>
import LeagueService from '@/services/LeagueService';
import Header from '@/components/Header.vue';
import { FLAGAPI_URL } from '@/utils/constants'
</script>
<template>
    <Header></Header>

    <table class="leader-board">
        <thead>
            <tr>
                <th>Team Name</th>
                <th>MP</th>
                <th>GF</th>
                <th>GA</th>
                <th>GD</th>
                <th>Points</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(match, index) in  matches " :key="index" :class="{ 'second': index % 2 }">
                <td>
                    <div class="home-team">
                        <img :src="FLAGAPI_URL + match.teamName + '.png'" class="country-flag" alt="Country Flag" />
                        <p class="country-name">{{ match.teamName }}</p>
                    </div>
                </td>
                <td>{{ match.matchesPlayed }}</td>
                <td>
                    {{ match.goalsFor }}
                </td>
                <td>
                    {{ match.goalsAgainst }}

                </td>
                <td>
                    {{ match.goalsFor - match.goalsAgainst }}
                </td>
                <td>
                    {{ match.points }}
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
    created() {
        const leagueService = new LeagueService();
        leagueService.fetchData().then(() => {
            this.matches = leagueService.getLeaderboard()
        })
    }

}
</script>
<style>
table.leader-board,
.leader-board tr,
.leader-board th,
.leader-board td {
    border-collapse: collapse;
}

table.leader-board,
table {
    width: 90%;
    font-family: sans-serif;
    margin-bottom: 10px;
    margin-left: auto;
    margin-right: auto;
}

.leader-board th {
    height: 40px;
    font-size: 12px;
    vertical-align: middle;
    background-color: #E4EDF2;
    padding: 0 18px;
}

.leader-board td {
    height: 70px;
    font-size: 14px;
    vertical-align: middle;
    padding: 0 18px;
}

.leader-board td img {
    width: 53px;
    height: 37px;
}


.leader-board tr th:nth-child(1),
.leader-board tr td:nth-child(1) {
    width: 45%;
    text-align: left;

}

.leader-board tr td:nth-child(1)>div {
    display: flex;
    align-items: center;
    column-gap: 22px;
    font-size: 16px;
    font-weight: 700;
    color: #182C62;
}


.leader-board tr th:nth-child(2),
.leader-board tr td:nth-child(2) {
    width: 10%;
    text-align: center;
}

.leader-board tr th:nth-child(3),
.leader-board tr td:nth-child(3) {
    width: 10%;
    text-align: center;
}

.leader-board tr th:nth-child(4),
.leader-board tr td:nth-child(4) {
    width: 10%;
    text-align: center;
}

.leader-board tr th:nth-child(6),
.leader-board tr td:nth-child(6) {
    width: 20%;
    text-align: center;

}

.leader-board tr th:nth-child(5),
.leader-board tr td:nth-child(5) {
    display: none;
}

.leader-board tr td:nth-child(6) {
    font-size: 16px;
    font-weight: 700;

    color: #025FEB;
}

.leader-board tr:nth-child(even) {
    background-color: unset;
}

@media only screen and (max-width: 750px) {}

@media only screen and (max-width: 500px) {

    .leader-board tr th:nth-child(5),
    .leader-board tr td:nth-child(5) {
        display: flex;
        width: 10%;
        align-items: center;
        justify-content: center;

    }

    .leader-board tr th:nth-child(3),
    .leader-board tr td:nth-child(3) {

        display: none;
    }

    .leader-board tr th:nth-child(4),
    .leader-board tr td:nth-child(4) {

        display: none;
    }

    .leader-board tr th:nth-child(1),
    .leader-board tr td:nth-child(1) {
        width: 85%;
        text-align: left;
    }

    .leader-board tr th:nth-child(5),
    .leader-board tr td:nth-child(5) {
        display: flex;
        width: 40%;
        align-items: center;
        justify-content: center;
    }
}
</style>