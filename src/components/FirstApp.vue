<template>
  <div id="app">
    <p>Date fr :</p> {{dateFr}}<br><br>

    <p>Date  Us:</p> {{dateUs}}<br><br>

    <div v-bind:id="id">
      <p v-text="textBrut"></p>
      <p v-html="textHtml"></p>
      <p v-text="personne.nom"></p>
      <p v-html="personne.prenom"></p>
      <p v-text="personne.age"></p>
    </div>
    <br><br>
    <input type="text" v-model="personne.prenom"> Bonjour {{personne.prenom}}
    <select v-model="ville">
      <option>Madrid</option>
      <option>Paris</option>
      <option>Rome</option>
    </select>
    Vous avez choisis {{ville}}
  </div>
  <input type="text" v-on:keyup="recopie" v-model="texte1">
  <input type="text" v-bind:value="texte2">
  <h1>Langage appris :</h1>
  <input type="checkbox" v-model="caseCocher" value="html"><label>Html</label>
  <input type="checkbox" v-model="caseCocher" value="css"><label>css</label>
  <input type="checkbox" v-model="caseCocher" value="js"><label>js</label>
  <br><br>
  <h3>{{caseCocher}}</h3>
  <h1>Langage préféré</h1>
  <input type="radio" v-model="favorite" value="html"><label>Html</label>
  <input type="radio" v-model="favorite" value="css"><label>css</label>
  <input type="radio" v-model="favorite" value="js"><label>js</label>
  <br><br>
  {{favorite}}
  <br><br>
  <h1 v-if="count > 1">Nombre de clics sur le bouton {{count}}</h1>
  <h1 v-else>Nombre de clic sur le bouton {{count}}</h1>
  <button v-on:click="count++">Incrémenter le compteur </button>
  <br><br>
  <img src="../assets/logo.svg" alt="logo"
       @click.left="largeur(200)"
       @click.right="largeur(100)"
       @click.middle="largeur(400)"
       @dblclick="largeur(300)"
       v-bind:width="valeur">
</template>

<script>

  export default {
  name: "FirstApp",
      data() {
        return {
          d: new Date(),
          url: "../assets/logo.svg",
          id: "vue",
          textBrut: "simple text",
          textHtml: "<font color ='red'><u>Un texte rouge souligné</u></font>",
          personne: {
            nom: "Snow",
            prenom: "Jon",
            age: 38
          },
          ville : '',
          texte1 : '',
          texte2 : '',
          caseCocher : [],
          favorite : '',
          count : 0,
          valeur : 300,

        }
      },
      computed: {
        dateFr() {
          return this.d.toLocaleTimeString();
        },

        dateUs() {
          return this.d.toLocaleTimeString('en-US')
        }
      },

    methods: {
      recopie() {
        this.texte2 = this.texte1.toUpperCase()
      },

      largeur(val) {
        this.valeur = val;
      }
    },







  }







</script>

<style scoped>

</style>