<template>
  <v-container class="fill-height">
    <v-row>
      <v-col cols="12" md="12" lg="12" sm="12">
        <v-tabs v-model="tab" bg-color="primary">
          <v-tab value="1.Gruppenphase">1.Gruppenphase</v-tab>
          <v-tab value="2.Gruppenphase">2.Gruppenphase</v-tab>
          <v-tab value="3.Gruppenphase">3.Gruppenphase</v-tab>
          <v-tab value="Achtelfinale">Achtelfinale</v-tab>
          <v-tab value="Viertelfinale">Viertelfinale</v-tab>
          <v-tab value="Halbfinale">Halbfinale</v-tab>
          <v-tab value="Finale">Finale</v-tab>
        </v-tabs>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" md="12" lg="12" sm="12">
        <v-tabs-window v-model="tab">
          <v-tabs-window-item value="1.Gruppenphase">
            <my-first-component
              v-for="match in groups.firstGroupStage"
              :key="match.matchID"
              :team-one="match.team1.teamName"
              :team-two="match.team2.teamName"
              :match-date="match.matchDateTime"
              :match-location="match.location.locationCity"
            ></my-first-component>
          </v-tabs-window-item>
          <v-tabs-window-item value="2.Gruppenphase">
            <my-first-component
              v-for="match in groups.secondGroupStage"
              :key="match.matchID"
              :team-one="match.team1.teamName"
              :team-two="match.team2.teamName"
              :match-date="match.matchDateTime"
              :match-location="match.location.locationCity"
            ></my-first-component>
          </v-tabs-window-item>
          <v-tabs-window-item value="3.Gruppenphase">
            <my-first-component
              v-for="match in groups.thirdGroupStage"
              :key="match.matchID"
              :team-one="match.team1.teamName"
              :team-two="match.team2.teamName"
              :match-date="match.matchDateTime"
              :match-location="match.location.locationCity"
            ></my-first-component
          ></v-tabs-window-item>
          <v-tabs-window-item value="Achtelfinale">
            <my-first-component
              v-for="match in groups.roundOf16"
              :key="match.matchID"
              :team-one="match.team1.teamName"
              :team-two="match.team2.teamName"
              :match-date="match.matchDateTime"
              :match-location="match.location.locationCity"
            ></my-first-component
          ></v-tabs-window-item>
          <v-tabs-window-item value="Viertelfinale">
            <my-first-component
              v-for="match in groups.roundOf8"
              :key="match.matchID"
              :team-one="match.team1.teamName"
              :team-two="match.team2.teamName"
              :match-date="match.matchDateTime"
              :match-location="match.location.locationCity"
            ></my-first-component
          ></v-tabs-window-item>
          <v-tabs-window-item value="Halbfinale">
            <my-first-component
              v-for="match in groups.roundOf4"
              :key="match.matchID"
              :team-one="match.team1.teamName"
              :team-two="match.team2.teamName"
              :match-date="match.matchDateTime"
              :match-location="match.location.locationCity"
            ></my-first-component
          ></v-tabs-window-item>
          <v-tabs-window-item value="Finale">
            <my-first-component
              v-for="match in groups.final"
              :key="match.matchID"
              :team-one="match.team1.teamName"
              :team-two="match.team2.teamName"
              :match-date="match.matchDateTime"
              :match-location="match.location.locationCity"
            ></my-first-component
          ></v-tabs-window-item>
        </v-tabs-window>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
let tab = ref("1.Gruppenphase");

const { data } = await useFetch(
  "https://api.openligadb.de/getmatchdata/em/2024/"
);
//match.location.locationCity
let groups = {
  firstGroupStage: [],
  secondGroupStage: [],
  thirdGroupStage: [],
  roundOf16: [],
  roundOf8: [],
  roundOf4: [],
  final: [],
};

for (const match of data.value) {
  if (match.group.groupName === "1. Runde Gruppenphase") {
    groups.firstGroupStage.push(match);
  }
  if (match.group.groupName === "2. Runde Gruppenphase") {
    groups.secondGroupStage.push(match);
  }
  if (match.group.groupName === "3. Runde Gruppenphase") {
    groups.thirdGroupStage.push(match);
  }
  if (match.group.groupName === "Achtelfinale") {
    groups.roundOf16.push(match);
  }
  if (match.group.groupName === "Viertelfinale") {
    groups.roundOf8.push(match);
  }
  if (match.group.groupName === "Halbfinale") {
    groups.roundOf4.push(match);
  }
  if (match.group.groupName === "Finale") {
    groups.final.push(match);
  }
}
</script>
