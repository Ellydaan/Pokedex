<template>

<body>
<div class=" container  align-items-start">
  <div class=" container row align-items-start">

    <div class="logo">
      <img src="../assets/logo.svg"  alt="logo"/>
      </div>

    <div class="bar">
      <input class="barre"
          type="text"
          v-model.trim="search"
          placeholder="Search pokemon..."
          @keyup="pokemonn"
      />
      <br />




</div>

    <div class="container row align-items-start row-cols-1 row-cols-sm-2 row-cols-lg-3  ">



      <div  v-for="pokemon in pokemon " :key="pokemon.id" >


        <div id="contenu1" >


          <div  :class="[pokemon.type1]" class="derriere">

            <p>HP <br>{{pokemon.hp}}

            </p>
            <p>ATTACK<br>{{pokemon.attack}} </p>
            <p>DEFENSE<br>{{pokemon.defense}} </p>
            <p>SP_ATTACK<br>{{pokemon.sp_attack}} </p>
            <p>SP_DEFENSE<br>{{pokemon.sp_defense}} </p>
            <p>SPEED<br>{{pokemon.speed}} </p>

            </div>


          <div :class="[pokemon.type1]" class="devant"  >

            <h5 class="card-title"> {{ pokemon.nom_pok}}  </h5>
            <br>

            <img role="poke" :src="pokemon.image_pok"  class="cardd" alt="img pokemon">

            <br>
            <br>
            <br>

            <h6>{{pokemon.type1}}<br>
              {{pokemon.type2}}<br>

            </h6>


          </div>



        </div>
        <div>




      </div>
    </div>

  </div>
</div>
</div>
</body>


</template>




<script>

import axios from "axios";
export default {

  name: 'pokemon',
  data() {
    return {
      pokemon: "",
      search: "",
      pokemonNoSearch:"",

    }
  },
  /***pokedex***/

  mounted() {
    axios
        .get('http://localhost:3001/pokedex')
        .then((reponse) => {
          this.pokemon = reponse.data;
          this.pokemonNoSearch= reponse.data
          console.log(this.pokemon)
        })
        .catch(error => {
      if (error.response) {
        window.location.replace("../login");
      }
    });
  },

  /***SEARCH***/

  methods: {

    pokemonn() {
      fetch("http://localhost:3001/pokedex")
          .then(response => response.json())
          .then(res => {
            if (this.search) {
              this.pokemon = res.filter(pokemon =>
                  pokemon.nom_pok.toLowerCase().includes(this.search.toLowerCase())
              )

            }

            else{
              this.pokemon = this.pokemonNoSearch
            }

          });
    }
  },


}









</script>





<style scoped>


.barre {
  width: 100%;

}

.barre{
 background: #EFEFBB;
  background: -webkit-linear-gradient(to top, #D4D3DD, #EFEFBB);
  background: linear-gradient(to bottom, #D4D3DD, #EFEFBB);;;
  width: 100%;
  border: 4px none #D4D3DD;
  border-bottom-style: solid;
  height: 50px;
  outline: none;
  color: #9DBFAF;

}

.barre{
  color: black;
@import url('http://fonts.cdnfonts.com/css/sf-pixelate');
  font-family: 'SF Pixelate', sans-serif;
}



/*Resize the wrap to see the search bar change!*/
.barre{
  width: 30%;

}

.container{
  width: 100%;
}








p,h5,h6{
  color: #262626;
  font-size: 30px;
@import url('http://fonts.cdnfonts.com/css/sf-pixelate');
  font-family: 'SF Pixelate', sans-serif;


}




img[role=poke]{
  height: 50%;
  width: 50%;


}

/***rotation 3D flip***/

#contenu1{
  color:hsla(0,0%,100%,.8);
  margin-top: 30px;
  -webkit-perspective:600px;
  perspective:600px}



#contenu1 div  {
  position:absolute;
  box-shadow:0 8px 5px hsla(0,0%,0%,.2);
  transition:.8s}


#contenu1 .derriere
{
  outline:1px solid transparent;
  overflow:hidden;
  backface-visibility:hidden;
  transform-style:preserve-3d;
  transform:rotatey(-180deg);
  -webkit-transform-style:preserve-3d;
  -webkit-backface-visibility:hidden;
  -webkit-transform:rotatey(-180deg)
}


#contenu1 div.devant
{
  outline:1px solid transparent;
  overflow:hidden;
  transform-style: preserve-3d;
  backface-visibility:hidden;
  -webkit-transform-style:preserve-3d;
  -webkit-backface-visibility:hidden;
}
#contenu1:hover .derriere
{
  transform:rotatey(0);
  -webkit-transform:rotatey(0)}


#contenu1:hover div.devant  {
  -webkit-transform:rotatey(180deg);
  transform:rotatey(180deg)}

.derriere p{
  color: #262626;
  word-wrap:break-word;
  text-align:center;
  font-size:18px;
  margin-top: 18px;


}



#contenu1 .derriere
{

  outline:1px solid transparent;
  overflow:hidden;
  backface-visibility:hidden;
  transform-style:preserve-3d;
  transform:rotatex(-180deg);
  -webkit-transform-style:preserve-3d;
  -webkit-backface-visibility:hidden;
  -webkit-transform:rotatey(-180deg)}

#contenu1:hover .derriere
{
  transform:rotatey(0);
  -webkit-transform:rotatey(0)}


#contenu1 {height:460px; margin-left: 10px}
#contenu1 div {width:100%;height:450px;}

/***COLOR CARD***/
.fire{
  background-color: #ffd1b5  ;
}
.water{
  background-color: #c2f3ff;
}
.grass{
  background-color: #d2f2c2  ;
}
.rock{
  background-color: #f0e09c ;
}
.electric{
  background-color: #fff1ba ;
}
.psychic{
  background-color: #ffc9da ;
}
.ghost{
  background-color: #dbbaff ;
}

.normal{
  background-color: #e6e6c3 ;
}
.fighting{
  background-color: #fcada9 ;
}
.ground{
  background-color: #e0ccb1 ;
}
.ice{
  background-color: #e8feff ;
}
.dragon{
  background-color: #c4bdff ;
}
.bug{
  background-color: #e0e8a2 ;
}
.poison{
  background-color: #f7cdf7 ;
}
.fairy{
  background-color: #ffdee5 ;
}
.flying{
  background-color: #eae3ff;
}



</style>




