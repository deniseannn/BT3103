<template>
  <div id=app>
    <h1>Add Item</h1>
    <form id="fm1">
        <label>Item Name</label>
        <input type="text" v-model.lazy="item.name" required/>

        <label>Item Brand</label>
        <input type="text" v-model.lazy="item.brand" placeholder="Enter if applicable"/>

        <label>Preferred Vendor</label>
        <select v-model="item.vendor">
          <option disabled value="">Select Vendor</option>
          <option>NTUC</option>
          <option>Cold Storage</option>
          <option>Sheng Siong</option>
        </select>
        
        <label>Item Category (Select all that applies)</label><br>
        <label for ="beverage">Beverage
        <input type="checkbox" id="beverage" value="Beverage" v-model="item.category"/></label>      
        <label for ="baked goods">Baked Goods
        <input type="checkbox" id="baked goods" value="Baked Goods" v-model="item.category"/></label>       
        <label for ="canned goods">Canned Goods
        <input type="checkbox" id="canned goods" value="Canned Goods" v-model="item.category"/></label>
        <label for ="dairy">Dairy
        <input type="checkbox" id="dairy" value="Dairy" v-model="item.category"/></label>
        <label for ="frozen">Frozen
        <input type="checkbox" id="frozen" value="Frozen" v-model="item.category"/></label>
        <label for ="produce">Produce
        <input type="checkbox" id="produce" value="Produce" v-model="item.category"/></label>
        <label for ="meat">Meat
        <input type="checkbox" id="meat" value="Meat" v-model="item.category"/></label>
        <label for ="others">Others
        <input type="checkbox" id="other" value="Others" v-model="item.category"/></label>
        <br>
        <button v-on:click.prevent="addItem">Add Item</button>
        
    </form>
  </div>
</template>

<script>
import database from '../firebase.js'
export default {

  data(){
    return{
        msg:"Add Item",
        item:{
          name:'',
          brand:'',
          vendor:'',
          category: []
        },
        
        
        }
  },
  methods:{
    addItem:  function () {
          //Save item to database
          database.collection('items').doc().set(this.item);
          this.item.name="";
          this.item.category=[];
          this.item.brand="";
          this.item.vendor="";
          alert("Item Added successfully. Customise Quanitity in Shopping Cart.")
          
        }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#app *{
    box-sizing: border-box;
}
#app{
    margin: 20px auto;
    max-width: 500px;
}

p{
    align-content: center;
    color:ivory;
}
label{
    display: inline-block;
    margin: 20px 0 10px;
    width:50%;
    align-content:left;

}
input[type="text"]{
    display: inline-block;
    padding: 8px;
    width:50%;
}



</style>