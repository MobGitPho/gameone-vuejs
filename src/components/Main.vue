<template>
  <div>
    <div class="main">
      <div v-if="screenWidth == 1" class="">
        <div id="next" class="next">
          <h3 class=" paraph ">
           {{title}}
          </h3>
          <div class=" paraphT">
            <div class="">
              <p> {{ paraph }}
              </p>
            </div>
          </div>
        </div>
      </div>

      <div class=" section">
        <div class=" content">
            <div class="mask"></div>
            <div class="first">
              <h1 class="paraph">
                {{ title }}
              </h1>
              <div class="paraphT">
                <div class="">
                  <p> {{ paraph }}</p>
                </div>
              </div>
              <div id="buttonM" class="row col-6 buttonM">
                <button type="button" id="BtnJ" data-toggle="modal" data-target="#exampleModalLong">Je M'inscris</button>
              </div>
            </div>
            <div class="blackimg">

            </div>
            <div class="imgm">
              <img src="@/assets/conso.jpg" alt="img" />
            </div>
          </div>
        </div>
      </div>
      <div id="caps" class="row col-12 caps ">

        <div id="buttonN" class=" col-12 buttonN">
          <button type="button" id="BtnJ" class="" data-toggle="modal" data-target="#exampleModalLong">Je
            M'inscris</button>
        </div>

      </div>


  </div>
  <div id="copp" class="cop">
    <p>copyright 2016-2022. GameOn inc.</p>
  </div>

</template>

<script>
import { ref } from 'vue'

export default {

  setup(){
      let title= ref('Marathon National de jeux videos');
      let paraph = ref('Vous aimez jouer? Notre prochain evenement gaming est ouvert aux reservations... Places limitees!');
      let screenWidth = ref(0);
      var x = window.matchMedia("(max-width: 540px)")
      SizeScreen(x)
      x.addListener(SizeScreen);

      function SizeScreen(x) {
        if (x.matches) {
          screenWidth.value = 1;
        }else{
          screenWidth.value = 0;
        }
      }

    return{
      title,
      paraph,
      SizeScreen,
      screenWidth,
      
    }
  }

}
</script>

<style lang="scss" scoped>
  .caps{
    display: none;
  }
  .section{
    width: 90%;
    height: 500px;
    margin-bottom: 0px;
    //border: 1px solid red;
    .content{
        width: auto;
        height: 450px;
        border-radius: 5px;
        background: #ffffff;
        color: #000;
        box-shadow: 0px 7px 5px 0px grey;
        position: relative;
        .blackimg{
          top: 0;
          float: left;
          width: 40%;
          height: 100%;
          background-color: rgba(0, 0, 0, 1);
          z-index: 1;
          position: absolute;
         
        }
        .imgm{
           float: right;
           width: 60%;
           border-radius: 5px;
            img{
              float: right;
              width: 60%;
              height: 100%;
              display: block;
              padding: 0;
              position: absolute;
              top: 0;
              right: 0;
              object-fit: cover;
            } 

        }
        
        .mask{
          top: 0;
          left: 0;
          width: 100%;
          height: 100%;
          position: absolute;
          background-color: rgba(121, 122, 124, 0.5);
        }
    }
    .first{
      z-index: 2;
      //border: 1px solid red;
      width: 40%;
      height: auto;
      .paraph{
        padding-top: 40px;
        color: rgba(255, 255, 255, 1);
        margin-top:30px;
        margin-left: 10px;
        width:450px;
        height:auto;
        z-index: 2;
        position: relative;
      }
      .paraphT{
        color: rgba(255, 255, 255, 1);
        padding-top:0px;
        padding-left: 0px;
        padding-bottom: 10px;
        margin-left: 10px;
        margin-bottom: 10px;
        margin-top: 20px;
        width:90%;
        height:auto;
        //border:1px solid yellow; 
        z-index: 2;
        position: relative;
        p{
          font-size: 18px;
        }
      }
      .buttonM{
        border: none;
        z-index: 2;
        position: relative;
        //border: 1px solid blue;
        width: auto;
        height: 50px;
        margin-top:50px;
        margin-left:0px;
        margin-bottom: 0px;
        button{
          border: none;
          height: auto;
          width: auto;
          color: #ffffff;
          padding-top: 10px;
          padding-bottom: 10px;
          padding-left: 30px;
          padding-right: 30px;
          background-color: rgba(204, 0, 0, 1);
          border-radius: 5px;
        }
      }
    }
   

    
    
  }

  .cop {
    float: left;
    background-color: #ffffff;
    color: rgba(204, 0, 0, 1);
    text-align: left;
    font-size: 12px;
    padding: 15px;
  }

  @media screen and (max-width: 540px) {
    .topnav a {display: none;}
    .topnav a.icon {
      float: right;
      display: block;
      margin-top: -15px;
    }
  .section{
    //border: 1px solid red;
    width: 100%;
    height: 500px;
    margin-bottom: 0px;
    
    .content{
        width: auto;
        height: 450px;
        //border: 1px solid blue;
        background: #ffffff;
        color: #000;
        //padding: 20px;
        box-shadow: 0px 0px 5px 0px black;
        position: relative;
        //z-index: -1;
        .blackimg{
          display: none;
          visibility: hidden;

        }
        .imgm{
           float: right;
           width: 100%;
           
            img{
                float: right;
                width: 100%;
                height: 100%;
                display: block;
                padding: 0;
                position: absolute;
                top: 0;
                left: 0;
                object-fit: cover;
            }

        }
        
        .mask{
          top: 0;
          left: 0;
          width: 100%;
          height: 100%;
          position: absolute;
          background-color: rgba(121, 122, 124, 0.5);
        }


    }
    .first{
      z-index: 2;
      //border: 1px solid red;
      width: 40%;
      height: auto;
      .paraph{
        display: none;
        /*color: rgba(255, 255, 255, 1);
        margin-top:30px;
        margin-left: 10px;
        width:450px;
        height:auto;
        z-index: 2;
        position: relative;*/
      }
      .paraphT{
        display: none;
       /* color: rgba(255, 255, 255, 1);
        padding-top:0px;
        padding-left: 0px;
        padding-bottom: 10px;
        margin-left: 10px;
        margin-bottom: 10px;
        margin-top: 20px;
        width:90%;
        height:auto;
        border:1px solid yellow; 
        z-index: 2;
        position: relative;*/
        p{
          font-size: 18px;
        }
      }
      .buttonM{
        display: none;
       /* border: none;
        z-index: 2;
        position: relative;
        //border: 1px solid blue;
        width: auto;
        height: 50px;
        margin-top:50px;
        margin-left:0px;
        margin-bottom: 0px;
        button{
          border: none;
          height: auto;
          width: auto;
          color: #ffffff;
          padding-top: 10px;
          padding-bottom: 10px;
          padding-left: 30px;
          padding-right: 30px;
          background-color: rgba(204, 0, 0, 1);
          border-radius: 5px;
        }*/
      }
    }
  }
  .caps{
    display: flex;
    align-items: center;
    justify-content: center;
    .buttonN{
      z-index: 1;
      border: none;
      width: auto;
      height: auto;
      margin-top:0px;
      margin-bottom: 0px;
      margin-left:0px;
      margin-right: 0px;
      button{
        border: none;
        height: auto;
        width: auto;
        color: #ffffff;
        padding-top: 10px;
        padding-bottom: 10px;
        padding-left: 30px;
        padding-right: 30px;
        background-color: rgba(204, 0, 0, 1);
        border-radius: 5px;
      }
    }
  }

  .cop {
    display: inline;
    justify-content: center;
    align-content: center;
    background-color: #ffffff;
    color: rgba(204, 0, 0, 1);
    text-align: center;
    font-size: 18px;
    padding: 15px;

    }

  .next{
    .paraph{
        padding-top: 10px;
        color: rgba(0, 0, 0, 1);
        margin-top:10px;
        margin-left: 10px;
        width:auto;
        height:auto;
        z-index: 2;
        position: relative;
      }
      .paraphT{
        color: rgba(0, 0, 0, 1);
        padding-top:0px;
        padding-left: 0px;
        padding-bottom: 10px;
        margin-left: 10px;
        margin-bottom: 10px;
        margin-top: 20px;
        width:auto;
        height:auto;
        //border:1px solid yellow; 
        z-index: 2;
        position: relative;
        p{
          font-size: 18px;
        }
      }

  
  }

 
}

@media screen and (min-width: 800px) {
  
  .paraphT{
    color: rgba(255, 255, 255, 1);
    padding-top:0px;
    padding-left: 0px;
    padding-bottom: 10px;
    margin-left: 10px;
    width:auto;
    height:auto;
    //border:1px solid yellow; 
    z-index: 2;
    position: relative;
    p{
      font-size: 20px;
    }
  }

  .buttonM{
    z-index: 2;
    position: relative;
    //border: 1px solid blue;
    width: auto;
    height: 40px;
    margin-top:2px;
    margin-left:0px;
    button{
      height: auto;
      width: auto;
      font-size: 25px;
      color: #ffffff;
      padding-top: 10px;
      padding-bottom: 10px;
      padding-left: 30px;
      padding-right: 30px;
      background-color: rgba(204, 0, 0, 1);
      border-radius: 9px;
    }
  }
  .cop {
    display: inline;
    justify-content: center;
    align-content: center;
    background-color: #ffffff;
    color: rgba(204, 0, 0, 1);
    text-align: center;
    font-size: 18px;
    padding: 15px;
    }
}

</style>