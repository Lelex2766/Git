<template>
  <div class="hello">
     <div id="root">
       <input type="text" v-model="newNote" required placeholder="note name">
      <input type="text" v-model="newInfo" required placeholder="note info">
      <button @click="created()">Add Note</button>
      <button id='seenotes' @click="getNote()" >Refresh</button>
      
      <ul v-for="(note,index) in notes" :key="note" >
        
        <li  v-text="note" class="main" > </li> <button  @click="seeInfo(index)">see Info</button> <button ids="" @click="open(ids[index])">Modify</button><button @click="deletes(ids[index])">Delete</button> <input  v-bind:class=ids[index] class="ids"   type="text" v-model="modifiedNote" required placeholder="new note name">
      <input v-bind:class=ids[index] class="ids"  type="text"  v-model="modifiedInfo" required  placeholder="new note info"><button v-bind:class=ids[index]   @click="modify(ids[index])" class="ids" >Confirm Modify</button>   <span v-bind:id=index  class="swag">{{infos[index]}}</span> 
      
      </ul>
    
      
      </div>
      <div>
    <div id='oui'> 
    </div>
        </div>       
  </div>
    
  
</template>

<script>

export default {
   
  
  
    data: function() {
      return {
        newNote: '',
        newInfo:'',
      notes: [],
      infos:[{}],
      swag:'',
      ids:[],
      modifiedInfo:'',
      modifiedNote:''
      
      }
    },
    beforeMount(){
    this.getNote();
  },
  methods: {
    open(){

    },
    async getNote(){
      const res = await fetch('http://postit.wac.under-wolf.eu/notes');
      const datas = await res.json();
      this.datas = datas;
      const yes = Object.entries(datas)[0][1];
      var length = yes.length
      this.notes = [];
      this.infos =[];
      this.ids =[];
      
      
      for (var i = 0; i < length; i++) {
    var hihi=yes[i].title;
    this.notes.push(hihi)
    var kek = yes[i].content
    this.infos.push(kek)
    var bebe=yes[i]._id
    this.ids.push(bebe)
    
}},


      
      
      
      
      
 async created() {
  // POST request using fetch with async/await
  const requestOptions = {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ title: ""+this.newNote,content:[""+this.newInfo] })
  };
  const response = await fetch("http://postit.wac.under-wolf.eu/notes", requestOptions);
  const data = await response.json();
  this.postId = data.id;
document.location.reload()
},
async modify(te) {
  // POST request using fetch with async/await
  const requestOptions = {
    method: "PUT",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ title: ""+this.modifiedNote,content:[""+this.modifiedInfo] })
  };
  const response = await fetch("http://postit.wac.under-wolf.eu/notes/"+te, requestOptions);
  const data = await response.json();
  this.postId = data.id;
document.location.reload()
},
async deletes(te) {
  // POST request using fetch with async/await
  const requestOptions = {
    method: "DELETE",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ title: ""+this.modifiedNote,content:[""+this.modifiedInfo] })
  };
  const response = await fetch("http://postit.wac.under-wolf.eu/notes/"+te, requestOptions);
  const data = await response.json();
  this.postId = data.id;
document.location.reload()
},
  
  
 
    
  
        addNote() {
          
        this.notes.push(this.newNote);
        this.infos.push(this.newInfo)
        this.newNote = '';
        this.newInfo='';
        this.x = this.x+1
      },
      seeInfo(index){
         if(
        document.getElementById(index).style.visibility=="visible"){
          document.getElementById(index).style.visibility="hidden"
        }
        
        else{document.getElementById(index).style.visibility="visible"
        

        }
      },
      
      hidden(index){

      },
      open(index){
         
       var dab=document.getElementsByClassName(index)
       for (var i=0;i<dab.length;i++){
         dab[i].classList.toggle("ids")
      
      }
     
}
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.swag{
  visibility:hidden;
  text-align: right;
}
.main{
  text-align: center;
  
}
.ids{
  visibility:hidden;
}
</style>
