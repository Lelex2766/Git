<template>
<div>
 <div class="header">
    <div class="one"><img class="logo" src="./images/nazrin.jpg"> 
        <input type="text" class="searchbar"  placeholder="Search..."><button class='searchbutton'><img src="./images/searchbutton.png" class="loupe"> </button><a href="http://localhost:8080/#/carting" class="cartbutton"><img src="./images/cart.png" class="imgcart">Cart Items</a><a href="http://localhost:8080/#/profile" class="profile"><img src="./images/profile.png" class="imgprofile"></a>
    </div>
    <div class="two">
        <div class="categories">Categories<a class="myButton" href="http://localhost:8080/#/">Logout</a> </div>
    </div>
    
</div>

<div class="carting">
    <img class="swaggy" src="./images/cart (1).png">
</div>
<div class="carting">Your articles</div>
    <div class="griding">
            <div class="griding1">Articles</div>
            <div class="griding2">Price</div>
            
    </div>
    <div  class="grid">
         <div class="grid1"></div>  
         <div class="grid2"></div> 
         <div class="grid3"></div> 
         <div class="grid4"></div> 
         <div class="grid5"></div>  
         <div class="grid6"></div> 
         <div class="grid7"></div> 
         <div class="grid8"></div> 
    </div>
<div class="gridingbis">
        <div class="grid1bis"></div>
        <div class="grid2bis"></div>
</div> 
</div>
</template>
<script>
export default {
    data: function() {
        return{
            nomdeloffres:['offre','superoffre']
        }
    }
    
}
</script>