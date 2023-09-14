// js
<script>
export default {
  name: "App",
  data() {
    return {
      title: "Welcome to Opportunity",
      sheet_id: import.meta.env.VITE_GOOGLE_SHEET_ID,
      api_token: import.meta.env.VITE_GOOGLE_API_KEY,
      entries: []
    };
  },

  computed: {

    currentDate() {
      const currentDate = new Date(); // erstelle mir das aktuelle Datum als Date-Objekt
      const day = currentDate.getDate(); // hole den Tag aus dem Date-Objekt
      const month = currentDate.getMonth() + 1; // hole den Monat aus dem Date-Objekt
      const year = currentDate.getFullYear(); // hole das Jahr aus dem Date-Objekt
      return day + "." + month + "." + year; // gib mir das Datum im Format DD.MM.YYYY zurück
    },
    
    gsheet_url() {
return `https://sheets.googleapis.com/v4/spreadsheets/${this.sheet_id}/values:batchGet?ranges=A2%3AE100&valueRenderOption=FORMATTED_VALUE&key=${this.api_token}`;
},


},

methods: {
    async getData() {
      const response = await fetch(this.gsheet_url);
      const data = await response.json();
      this.entries = data.valueRanges[0].values;
    }
},

mounted() {
    this.getData(); // get first initial data and then wait for the next update
},


}


</script>


// html
<template>
  <div id="application">
    <header>
      <h1 class="site-title">{{ title }}</h1>
      <p class="date">{{currentDate}}</p>
    </header>


    <ul>
      <li class="event" v-for="entry in entries">
        <p class="time"> {{entry[0]}}, {{entry[1]}}</p>
        <p class="event-content title"> {{entry[2]}}</p>
        <p class="event-content">{{entry[3]}}</p>
      </li>


    
      
    </ul>





    <footer class="footer">
      <div  class="logos">
        <img class="logopic" src="./assets/STZH_SEB_Logo.png" alt="Footer Logo">
        <img class="logopic" src="./assets/Opportunity.png" alt="Footer Logo">
        <img class="logopic" src="./assets/SAG_Logo_De.png" alt="Footer Logo">
      </div>
    </footer>
  
  </div>
  </template>  


// css
<style>
#application {
  font-family: "Inter", sans-serif;
  -webkit-font-smoothing: antialiased; 
  margin-top: 20px;
  max-width: 960px;
  margin-left: auto;
  margin-right: auto;
  }

  ul {
    padding: 0px;
  }

header {
  margin-bottom: 20px;
}

body {
  background-color: #E8EFF4;
} 

.site-title {
  font-size: 62px;
  margin-bottom: 0px;
}

.date {
  color: #9AA7B1;
  font-size: 62px;
  margin-top: 18px;
  margin-bottom: 30px;
}

.event {
  background-color: #0F05A0; /* Dunkelblauer Hintergrund für die Ereignisse */
  color: #FFBFAB; /* Lachs Schriftfarbe */
  border-radius: 5px;
  margin-bottom: 40px;
  padding: 30px;
}


.time {
  color: #EB5E00;
  font-size: 28px;
  font-weight: 900;
}

.event-content {
  color: #FFBFAB;
  font-size: 28px;
}

.event-content.title {
  font-weight: 900;
}



/* Stil für Bilder im Footer */
.footer {
  position: fixed;
  bottom: 0;
  left:0;
  width: 100%;
  height: 70px;
  background-color: white;
  flex-direction: row;
}

.logos {
  display: flex;
  justify-content: space-around;
  height: fit-content;
}

.logopic {
  width: 200px;
  height: 50px;
  margin: 10px;
}
ul {
  list-style-type: none;
}
</style>


