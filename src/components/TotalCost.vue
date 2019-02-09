<template>
   <div>
     <p>Liste des articles</p>

     <div class="container-main">
         <div class="wrapper-article">
             <div class="container-articles">
                 <div class="article-one"> 
                     <ul>
                         <li v-for="article in listClothes" 
                            class = "item-article" @click = "changeActive(article)"
                            :class="{active: article.active}">

                            <div>{{ article.name }}</div>
                            <div> {{ article.price | currency }}</div>

                         </li>
                     </ul>
                     <div class="total-panel">
                         <div>Sous Total </div>
                         <div> {{ total(listClothes)  | currency}}</div>
                    </div>
                </div> 

                <div class="article-one">
                    <ul>
                        <li v-for="article in listFood" 
                            class = "item-article" @click = "changeActive(article)"
                            :class="{active: article.active}">

                            <div>{{ article.name }}</div>
                            <div> {{ article.price  | currency }}</div>

                        </li>
                    </ul>
                    <div class="total-panel">
                        <div>Sous Total </div>
                        <div> {{ total(listFood) | currency}}</div>
                    </div>
                </div>
           </div>

           <div class="total-all">
              {{ TotalAll() | currency }}
           </div>
        
        </div>


        
     </div>
     


   </div>
</template>

<script>


export default {
    name: 'total-cost',
    
    

    data() {
        
        
        return {
            
            Somme: 0,
           // TotalAll: 0,
         
        listClothes: [
            {'name': 'Blouson', 'price': 310, active: true },
            {'name': 'Manteau', 'price': 120, active: false},
            {'name': 'Robe', 'price': 640, active: false}



        ],

        listFood: [
            {'name': 'Cheese', 'price': 10, active: true },
            {'name': 'Drink', 'price': 50, active: false},
            {'name': 'Robe', 'price': 40, active: false}



        ]
        }
    },

    methods: {
       changeActive(s) {
           s.active = !s.active;

           
        },

        

        total(articeCategory) {
            var letotal = 0;
            articeCategory.forEach(function(itemCurrent){
                 
                 if(itemCurrent.active) {
                     letotal += itemCurrent.price ;
                     
                      
                 }
            });
            
            return letotal;
        },

        TotalAll() {
           return this.total(this.listClothes) + this.total(this.listFood);
        
        }


    },

    filters: {
       currency:  function(value) {
         return value + ' Euro';
        }
    }

    
}
</script>

<style>
ul {
    list-style-type: none;
    padding: 0;
}

li {
    background-color: #34495E;
    border: 1px solid #1F618D;
}

li.active {
    background-color: #F39C12;
}

.container-main {

    display: flex;
    justify-content: space-between;
}
.wrapper-article {
    width: 600px;
    margin: 0 auto;
}
.container-articles {
     display: flex;
     flex: 1 0 auto;
     justify-content: space-between;
     
}

.article-one {
    width: 40%;
}
.total-all {
    background-color: #328bf2;
    color: white;
    margin-top: 20px;
    height: 60px;
    line-height: 60px;
    font-size: 28px;
}
.item-article {
    border-radius: 5px;
    margin-bottom: 10px;
    padding: 10px;
    font-size: 20px;
    color: #FFF;
    display: flex;
    flex: 1 0 auto;
    justify-content: space-between;

}

.total-panel {
    display: flex;
    justify-content: space-between;
    padding: 10px;
    background-color: #1644ad;
    color: white;

}

</style>