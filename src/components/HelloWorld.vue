<template>
  <div class="app">
    <div class="header">
      <a href="#default" class="logo">Movies</a>
      <div class="header-right">
        <a class="active" id="myBtn" href="#">Add Movies</a>
      </div>
    </div> 
     
    <!-- <div class="columns is-multiline" > -->
         <!-- <template>
            < <div id="movie" class="a"> -->
               
            <!-- </div> -->
        <!-- </template> -->
        <div v-for="mov in movies" :key="mov.id" class="column is-one-third"  > 
          <br>
          <br>
          <!-- //onclick="movieSelected('{{mov.imdbID}}')" -->
                <!-- <div class="container"> -->
           
            <!-- <a href="#" onClick="showStuff()" ><img  :src="mov.Poster" style="display: inline-block" /></a>
            <div id="hidden" style="display: none"><p @onclick="showMovie('{{mov.imdbID}}')"
            
            >Movie Name : {{mov.Title}},<br> Movie Year : {{mov.Year}}</p> 
          </div> -->
           
           <!-- <a href="#" @click="getmovies()"><img :src="mov.Poster" style="display: inline-block"></a> -->

         
             <a href="##" @click="showMovie(mov.imdbID)"><img :src="mov.Poster" class= "a" style="display: inline-block">
             </a>
          
           
            

        <!-- <h5>{{mov.Title}}</h5> -->
      
      </div>
      <div id="hidden" style="display: none" class="a"><div id="movie"></div></div>
    


    <div id="myModal" class="modal">
      <div class="modal-content">
        <span class="close">&times;</span>
        <h5> ADD A NEW MOVIE </h5>
        <hr>
        <div class="row">
          <div class="col-25">
            <label for="fname">Movie Name</label>
          </div>
          <div class="col-75">
            <input type="text" id="fname" name="Moviename" placeholder="Enter Movie name.." />
          </div>
        </div>
        <div class="row">
          <div class="col-25">
            <label for="lname">Movie URL</label>
          </div>
          <div class="col-75">
            <input type="text" id="lname" name="MovieURL" placeholder="Enter Movie URL">
          </div>
        </div>
        <div class="row">
          <div class="col-25">
            <label for="subject">Summary</label>
          </div>
          <div class="col-75">
            <textarea id="subject" name="subject" placeholder="Movie Summary.." style="height:100px"></textarea>
          </div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import axios from 'axios'
// import $ from 'jquery'

// import $ from 'jquery'
// let $ = jquery,
export default {   
  data(){
      return  {
        movies:null,
       
      }
  },
  methods : {
       showMovie(id) {
       sessionStorage.setItem('movieId', id);
        let movieId = sessionStorage.getItem('movieId');
         axios.get('http://www.omdbapi.com/?i='+movieId+'&apikey=9be27fce').then(
  (response) => {
    let movie = response.data;
    
      var output = `
      <div class="row">
        <h6>${movie.Title}</h6>
    `;
   document.querySelector('#movie').innerHTML = output;
    console.log(output);
  }
);
        //  axios.get('http://www.omdbapi.com?i='+movieId).then((response)=>{
        // console.log(response);
        //  });

      //  window.location = '';
      //  return false;
  //      var movies = response.data.Search;
  //    $(document).ready(function(){
  //   $('#myImg').click(function(){
     
  //   });

  //  });   
    },
     showStuff()  {
  let hidden = document.getElementById('hidden');
  if (hidden.style.display == "none") {
    hidden.style.display = "block"
  } else {
    hidden.style.display = "none"
  }
}

    // getmovies(){
    //   let movieId = sessionStorage.getItem('movieId');
    //   console.log(movieId);
    //   // axios.get('http://www.omdbapi.com/?s='+movieId).then((response)=>{
    //   //   console.log(response);
    //   // });
    // }
   

  },
 
  
  mounted(){
    // this.$root.$on('HelloWorld',()=>{this.showMovie})
    axios.get('http://www.omdbapi.com/?s=harry potter&apikey=e0620bd4')
    .then(response =>(this.movies = response.data.Search))
  },


}

</script>

<style scoped>


.popup {
  position: relative;
  display: inline-block;
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* The actual popup */
.popup .popuptext {
  visibility: hidden;
  width: 160px;
  background-color: #555;
  color: #fff;
  text-align: center;
  border-radius: 6px;
  padding: 8px 0;
  position: absolute;
  z-index: 1;
  bottom: 125%;
  left: 50%;
  margin-left: -80px;
}

/* Popup arrow */
.popup .popuptext::after {
  content: "";
  position: absolute;
  top: 100%;
  left: 50%;
  margin-left: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: #555 transparent transparent transparent;
}

/* Toggle this class - hide and show the popup */
.popup .show {
  visibility: visible;
  -webkit-animation: fadeIn 1s;
  animation: fadeIn 1s;
}

/* Add animation (fade in the popup) */
@-webkit-keyframes fadeIn {
  from {opacity: 0;} 
  to {opacity: 1;}
}

@keyframes fadeIn {
  from {opacity: 0;}
  to {opacity:1 ;}
}



/*original*/
input[type=text], select, textarea {
  width: 90%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  resize: vertical;
}

label {
  padding: 12px 12px 12px 0;
  display: inline-block;
}

input[type=submit] {
  background-color: #4CAF50;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  float: right;
}

input[type=submit]:hover {
  background-color: #45a049;
}

.container {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}

.col-25 {
  float: left;
  width: 25%;
  margin-top: 6px;
}

.col-75 {
  float: left;
  width: 75%;
  margin-top: 6px;
}

/* Clear floats after the columns */
.row:after {
  content: "";
  display: table;
  clear: both;
}

/* Responsive layout - when the screen is less than 600px wide, make the two columns stack on top of each other instead of next to each other */
@media screen and (max-width: 600px) {
  .col-25, .col-75, input[type=submit] {
    width: 100%;
    margin-top: 0;
  }
}

.grid-container {
  display: grid;
  height: 400px;
  align-content: center;
  grid-template-columns: auto auto auto;
  grid-gap: 15px;
  /* background-color: #2196F3; */
  padding: 40px;
}

.grid-container > div {
  background-color: rgba(255, 255, 255, 0.8);
  text-align: center;
  padding: 20px 0;
  font-size: 30px;
}
.header {
  overflow: hidden;
  background-color: #f1f1f1;
  padding: 5px 10px;
}

.header a {
  float: left;
  color:crimson;
  text-align: center;
  padding: 12px;
  text-decoration: none;
  font-size: 18px; 
  line-height: 25px;
  border-radius: 4px;
}

.header a.logo {
  font-size: 25px;
  font-weight: bold;
}

.header a:hover {
  background-color: #ddd;
  color: black;
}

.header a.active {
  background-color: crimson;
  color: white;
}

.header-right {
  float: right;
}

@media screen and (max-width: 500px) {
  .header a {
    float: none;
    display: block;
    text-align: left;
  }
  
  .header-right {
    float: none;
  }
}

.card {
  box-shadow: 0 4px 4px 0 rgba(0,0,0,0.2);
  transition: 0.3s; 
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(209, 22, 22, 0.2);
}

.container {
  padding: 0px 0px; 
 } 

img {
  height: 500px;
  width: 300px;
  border-radius: 8px;
}
/* #myInput {
  background-image: url('/css/searchicon.png');
  background-position: 10px 12px;
  background-repeat: no-repeat;
  width: 90%;
  font-size: 16px;
  padding: 12px 20px 12px 40px;
  border: 1px solid #ddd;
  margin-bottom: 12px;
} */

/* * {
  box-sizing: border-box;
} */

/* body {
  font-family: Arial, Helvetica, sans-serif;
} */

/* Float four columns side by side */
.column {
  float: left;
  width: 25%;
  /* padding: 50 50px; */
 
}

/* Remove extra left and right margins, due to padding */
.row {margin: 0 -5px;}

/* Clear floats after the columns */
.row:after {
  content: "";
  display: table;
  clear: both;
}

/* Responsive columns */
@media screen and (max-width: 600px) {
  .column {
    width: 100%;
    display: block;
    margin-bottom: 20px;
  }
}

/* Style the counter cards */
/* .card {
  box-shadow: 0 0px 0px 0 rgba(0, 0, 0, 0.2);
  padding: 1px;
  text-align: center;
  background-color: #f1f1f1;
} */

h5{
  font-family: Georgia, 'Times New Roman', Times, serif ;
  /* font-style: oblique; */
   color : #DC143C;
   
  
}


.modal {
  display: none; /* Hidden by default */
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  padding-top: 100px; /* Location of the box */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
  background-color: rgb(0,0,0); /* Fallback color */
  background-color: rgba(0,0,0,0.4); /* Black w/ opacity */
}

/* Modal Content */
.modal-content {
  background-color: #fefefe;
  margin: auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
}

/* The Close Button */
.close {
  color: #aaaaaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
}
</style>