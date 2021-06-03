<template>
 <div class ="whole" v-if= "loaded">
        <section class="text-3xl flex justify-counter content-center flex-col mx-auto text-center"></section>
        <h3 v-if = "!expired"><b>HUGE DISCOUNT</b></h3>
        <h5 v-else> Timer Is Done </h5> 
      <p> <section class="flex text-6xl justify-center content-center">
          <div class="days  mr-2 relative">  
               {{ displayDays}}
              <div class="label  text-sm absolute bottom-0">days</div>       
          </div>
          <span class="leading-snug">:</span>
          <div class="hours mx-2 relative">
               {{ displayHours}}
          <div class="label text-sm absolute bottom-0">hours</div>       
       </div>
       <span class="leading-snug">:</span>
          <div class="minutes mx-2 relative">
               {{ displayMinutes}}
               <div class="label text-sm absolute bottom-0">minutes</div>       
       </div>
       <span class="leading-snug">:</span>
          <div class="seconds ml-2 relative">
               {{ displaySeconds}}
               <div class="label text-sm absolute bottom-0">seconds</div>       
       </div>
        </section>
        </p>
        <img class="bmw" src="https://cdn.wallpapersafari.com/58/24/HuOX2p.jpg" alt="Girl in a jacket" width="470">
         <img id="sport" src="https://corsameccanica.com/content/images/thumbs/0010345_2015-honda-cbr-1000rr-sp.jpeg" alt="Girl in a jacket" position="left" width="550">
        <img class="bike" src="http://3.bp.blogspot.com/-3MInA1NBSro/TuNUhIV0tTI/AAAAAAAAANQ/HKQsHk4dNmc/w1200-h630-p-k-no-nu/HONDA-wallpaper_2006-Interceptor_motorcycle_1.jpg" alt="Girl in a jacket" width="550" >
        <img class="car" src="https://cdn.wallpapersafari.com/58/24/HuOX2p.jpg" alt="Girl in a jacket" width="600" >
         <img id="motor" src="https://corsameccanica.com/content/images/thumbs/0010345_2015-honda-cbr-1000rr-sp.jpeg" alt="Girl in a jacket" position="left" width="470">
       <img class="like" src="http://3.bp.blogspot.com/-3MInA1NBSro/TuNUhIV0tTI/AAAAAAAAANQ/HKQsHk4dNmc/w1200-h630-p-k-no-nu/HONDA-wallpaper_2006-Interceptor_motorcycle_1.jpg" alt="Girl in a jacket" width="930" > 
         <img id="best" src="https://cdn.pixabay.com/photo/2015/04/04/18/51/offer-706845_960_720.jpg" alt="Girl in a jacket" width="550" height="100"  >
</div>
    
</template>

<script>
    export default {
          props: ['year', 'month', 'date', 'hour', 'minute', 'second', 'millisecond'],
        data: () => ({
            displayDays: 0,
            displayHours: 0,
            displayMinutes: 0,
            displaySeconds: 0,
            loaded: false,
            expired: false
        }),
        computed: {
            _seconds: ()=> 1000,
            _minutes() {
                return this._seconds*60;
            },
            _hours() {
                return this._minutes*60;
            },
            _days() {
                return this._hours*24;
            },
            end() {
                return new Date(
                    this.year,
                    this.month,
                    this.date,
                    this.hour,
                    this.minute,
                    this.second,
                    this.millisecond
                );
            }
            
        },
        mounted(){
            this.showRemaining();
        },
        methods: {
            formatNum: num => ( num < 10 ? "0" + num: num),

            showRemaining() {
             const timer = setInterval(()=> {
                 const now = new Date();
                 //const end = new Date(2020, 11,  10, 59, 59, 31);
                 const distance = this.end.getTime() - now.getTime();
                 if(distance < 0){
                     clearInterval(timer);
                     this.loaded= true,
                     this.expired= true
                     return;
                 }

                 const days = Math.floor(distance / this._days);
                 const hours = Math.floor((distance % this._days) / this._hours);
                 const minutes = Math.floor((distance % this._hours) / this._minutes);
                 const seconds = Math.floor((distance % this._minutes) / this._seconds);
                this.displayDays = this.formatNum(days);     
                this.displayHours = this.formatNum(hours);
                this.displayMinutes = this.formatNum(minutes);
                this.displaySeconds = this.formatNum(seconds);
                this.loaded= true;
               }, 1000);
            }

        }
       
               
    };
     
</script>

<style scoped>
.seconds{
    max-width: 60px;
}
.whole{
  background-image: linear-gradient(tomato, pink, tomato);
  height: 800px;
  margin-top:-70px;


}
h3{
    font-size:50px;
    margin-left:80px;
    text-align:center;
    margin-top:50px;
}
h5{
    font-size:50px;
    margin-left:80px;
    text-align:center;
    margin-top:50px;
}
.bike{
   height:250px; 
   margin-top:-30px;
}
#motor{
    height:250px;
    float:right;
    width:470px;
    margin-top:-500px;
}
.bmw{
    height:250px; 
    float:right;
    width:550;
     margin-top:-250px;
}
#sport{
    height:250px; 
    width:250;
    margin-top:-250px;
    float:top right;
}
.car{
    height:280px;
   
}
#best{
    float:right ;
    background-color:tomato;
    height:250px;
    margin-top:-500px;
    margin-right:470px;

    

}
.like{
    float:center;
    margin-left: 600px;
    height:250px;
    margin-top:-250px;
    
}
p{
    height:100px;
    width:500px;
    background-image: linear-gradient(tomato);
    box-shadow:  inset 0  0 10px #000000;
    color:white;
    font: size 60px;
    box-align: justify;
    margin-top:30px;
    margin-left: 550px;
    box-shadow: 1px 1px 0px #000,
                2px 2px 0px #000,
                3px 3px 0px #000,
                4px 4px 0px #000,
                5px 5px 0px #000,
                6px 6px 0px #000,
       
}

</style>