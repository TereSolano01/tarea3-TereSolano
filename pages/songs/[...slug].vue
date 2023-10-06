<!-- pages/books/[...slug].vue -->
<template>
  <div class="container">
    <HeaderView />
    <div class="row">
      <div class="three columns"></div>
      <div class="six columns">
        <div class="song-card">
          <h2>{{song.track_name}}</h2>
          <div class="song-info">
            <table id="songInfoTable" class="display centered">
              <tbody>
                <tr>
                  <td><p class="bold">Artista(s):</p></td>
                  <td><p>{{song.artist_name}}</p></td>
                </tr>
                <tr>
                  <td><p class="bold">Año de lanzamiento:</p></td>
                  <td><p>{{song.released_year}}</p></td>
                </tr>
                <tr>
                  <td><p class="bold">Reproducciones:</p></td>
                  <td><p>{{ formatoNumero(song.streams) }}</p></td>
                </tr>
                <tr>
                  <td><p class="bold">Porcentaje bailable:</p></td>
                  <td><p>{{song.danceability}}%</p></td>
                </tr>
                <tr>
                  <td><p class="bold">Porcentaje acústico:</p></td>
                  <td><p>{{song.acousticness}}%</p></td>
                </tr>
                <tr>
                  <td><p class="bold">Porcentaje de energía:</p></td>
                  <td><p>{{song.energy}}%</p></td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
      <div class="three columns"></div>
    </div>
    <FooterView />
  </div>
</template>
  <script setup>
    const route = useRoute()
    const songs = await queryContent('songs').only('items').findOne()
    const song = songs.items.find(song => song.slug == route.params.slug)
  </script>

<script>
export default {
  methods: {
    formatoNumero(numero) {
      return numero.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    }
  }
}
</script>

<style scoped>
@import url('../../static/css/indexSongs.css');
  </style>