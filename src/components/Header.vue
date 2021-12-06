<template class="header">
  <h1>Projekat iz predmeta PABP - web aplikacija realizovana pomoću Vue.js radnog okvira</h1>
  <p><b>Ovaj deo je komponenta header.</b></p>
  <p>Ova aplikacija treba da, u suštini, "povuče" (metodom GET) podatke o kategorijama i proizvodima 
    iz datog Northwind API-ja.</p> 

  <p>Pribavljene podatke onda treba prikazati u tabelarnom prikazu.</p>

  <p>Potom treba omogućiti funkciju da se za izabranu kategoriju proizvoda u listi prikažu 
    svi proizvodi koji pripadaju toj kategoriji. 
    Ovde je potrebno omogućiti i dodavanje novog proizvoda u izabranu kategoriju.</p>

  <p>Potom, treba omogućiti da se klikom na neki proizvod, pomoću metode GET prikažu detalji o izabranom proizvodu (dodati i ukupnu vrednost proizvoda UnitPrice*UnitsInStock),
    kao i da se korišćenjem metoda POST, PUT i DELETE izabrani proizvod može izmeniti, sačuvati realizovana izmena, 
    kao i da se proizvod može obrisati, ukoliko je to ono što želimo.</p>

  <p>Pored svega ovoga, potrebno je omogućiti i filtriranje prikaza proizvoda po dobavljačima, 
    kao i pretragu proizvoda po vrednosti(UnitPrice) gde se prikazuje lista ili tabela sa svim prozivodima do unete vrednsti.</p>

</template>

<script>
  export default {
    name: 'Header'
  }
</script>

<style>
.header {
  color: blueviolet;
  font-style: oblique;
  text-align: left;
}
</style>