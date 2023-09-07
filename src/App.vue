// js
<script>
export default {
  name: "App",
  data() {
    return {
      title: "Welcome to Opportunity",
      sheet_id: import.meta.env.VITE_GOOGLE_SHEET_ID,
      api_token: import.meta.env.VITE_GOOGLE_API_KEY,
    }
  },

  computed: {

    currentDate() {
      const currentDate = new Date(); // erstelle mir das aktuelle Datum als Date-Objekt
      const day = currentDate.getDate(); // hole den Tag aus dem Date-Objekt
      const month = currentDate.getMonth() + 1; // hole den Monat aus dem Date-Objekt
      const year = currentDate.getFullYear(); // hole das Jahr aus dem Date-Objekt
      return day + "." + month + "." + year; // gib mir das Datum im Format DD.MM.YYYY zurück
    }
  }
};

</script>


// html
<template>
  <div id="app">
    <header>
      <h1 class="site-title">{{ title }}</h1>
      <p>{{currentDate}}</p>
    </header>


  <ul>
    <li class="event">
      <p class="time">14:00Uhr</p>
      <p>Basisbeschäftigung Besuch</p>
      <p>Interessierte für den zweiten Kurs werden uns besuchen</p>
      </li>


  
      <li class="event">
        <p>14:00Uhr</p>
        <p>Basisbeschäftigung Besuch</p>
        <p>Interessierte für den zweiten Kurs werden uns besuchen</p>
      </li>  



  
      <li class="event">
        <p>14:00Uhr</p>
        <p>Basisbeschäftigung Besuch</p>
        <p>Interessierte für den zweiten Kurs werden uns besuchen</p>
      </li>
  

  </ul>





    <footer>
        <img src="./assets/STZH_SEB_Logo.png" alt="Footer Logo">
        <img src="./assets/Opportunity.png" alt="Footer Logo">
        <img src="./assets/SAG_Logo_De.png" alt="Footer Logo">
    </footer>
  
  
  
  </div>
</template>



// css
<style>
#app {
  font-family: "Inter", Medium, Black;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #323d4a;
  margin: 60px;
  background-color: #E8EFF4; /* Hellblauer Hintergrund */
  padding: 20px; /* Abstand um den Inhalt */
}

header {
  text-align: center;
  margin-bottom: 20px;
}

.site-title {
  font-size: 2.5rem;
}

.event {
  background-color: #0F05A0; /* Dunkelblauer Hintergrund für die Ereignisse */
  color: #fff; /* Weiße Schriftfarbe */
  border-radius: 5px;
  margin-bottom: 20px;
  padding: 10px;
}

.event-header {
  text-align: center;
}

.event-content {
  padding: 10px;
}

footer {
  text-align: center;
  margin-top: 20px;
}

/* Stil für Bilder im Footer */
footer img {
  max-width: 100px;
  margin: 10px;
}
</style>


