<template>
    <div v-if="Modalbox == 0"  class="modal fade " id="exampleModalLong" tabindex="-1" role="dialog" aria-labelledby="exampleModalLongTitle"
    aria-hidden="true">
 
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div id="bclose" class="modal-header">

          <button type="button" class="close" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body">

          <form @submit.prevent=" validateForm()" name="Form" >
            <div id="Form" v-if="resultForm == 0">
              <label for="Prenoms">Prenoms</label>
              <input type="text" id="fname" name="Prenoms" minlength="4" pattern="^[A-Za-z]+$" v-model="lastnameUser">
              <label id="fNom" class="falseM">{{ fNom }}</label><br>

              <label for="Nom">Nom</label>
              <input type="text" id="lname" name="Nom" minlength="4" pattern="^[A-Za-z]+$" v-model="nameUser">
              <label id="Nom" class="falseM">{{ Nom }}</label><br>

              <label for="Email">Email</label>
              <input type="email" id="lname" name="Email" placeholder="johndoe@gmail.com" v-model="mailUser">
              <label id="femail" class="falseM">{{ femail }}</label><br>

              <label for="Dtn">Date de naissance</label>
              <input type="date" id="Dtn" name="Dtn" onchange="" v-model="dateUser">
              <label id="fDtn" class="falseM">{{ fDtn }}</label><br>

              <label for="Cmb">A combien de tournois GameOn avez vous déjà participé?</label>
              <input type="number" min="0" id="lname" name="Cmb" v-model="nbgameUser" >
              <label id="fCmb" class="falseM">{{ fCmb }}</label><br>

              <label for="radio">A quel tournoi souhaitez-vous participer cette année?</label>
              <label id="fradio" class="falseM"></label><br>
              <div class="">
                <div class="radiob" v-for="rad in radios" :key="rad">
                    <input  type="radio" id="radio" name="radio" value='' > <span> {{ rad.name }} </span>      
                    
                </div>
               
                <!--input type="radio" id="radio" name="radio" value="San Francisco">&nbsp; San Francisco
                &nbsp;&nbsp;&nbsp;
                <input type="radio" id="radio" name="radio" value="Seattle">&nbsp; Seattle
                &nbsp;&nbsp;&nbsp;&nbsp;
                <input type="radio" id="radio" name="radio" value="Chicago">&nbsp; Chicago
                &nbsp;&nbsp;&nbsp;
                <input type="radio" id="radio" name="radio" value="Boston">&nbsp; Boston
                &nbsp;&nbsp;&nbsp;
                <input type="radio" id="radio" name="radio" value="Portland" &nbsp; Portland-->

              </div>
              <div class="">
                <input type="checkbox" id="Accept" name="checkboxA" true-value="yes" false-value="no" v-model="checkedA">&nbsp; J'ai
                lu et accepté les conditions d'utilisations<br>
                <input type="checkbox" id="Prevent" name="checkboxP" value="Prevent">&nbsp; Je souhaites
                être prévenu des prochains évenements.
              </div>
              <label id="fCheckA" class="falseM">{{ fCheckA }}</label><br>
            </div>
            <div id="FormS" v-if="resultForm == 1">
              <p id="psucces">{{ psucces }}</p>

            </div>

            <div class="text-center" v-if="resultForm == 0">
              <button type="submit" id="btnMod" class="btn btn-danger btn-lg text-center">C'est
                parti</button>
            </div>

          </form>


        </div>
        <div class="btnModF" v-if="resultForm == 1">
            <button type="button" class="btn btn-danger btn-lg text-center" @click="FermeModal">Fermer</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {

    setup(){
        var DtA = new Date();
        var yr = DtA.getFullYear();

        let lastnameUser = ref('');
        let nameUser = ref('');
        let mailUser= ref('');
        let dateUser = ref('');
        let nbgameUser = ref('');
        let checkedA = ref('');
        let fNom = ref('');
        let Nom = ref('');
        let femail = ref('');
        let fDtn = ref('');
        let fCmb = ref('');
        let fCheckA= ref('');
        let resultForm = ref(0);
        let psucces = ref('');
        let Modalbox = ref(0);

        let radios = [
            {name:'New york'},
            {name:' San Francisco'},
            {name:'Seattle'},
            {name:'Chicago'},
            {name:'Boston'},
            {name:'Portland'}
        ]
        console.log('radios',radios)
        let validateForm = function(){
            //console.log(lastnameUser.value)
            if (lastnameUser.value == "" || (lastnameUser.value.length <= 3)) {
                fNom.value = "Le prénoms doit contenir au moins 4 caractères et uniquement alphabétique";
                
                //fname.focus();
                return false;
            } else {
               
               fNom.value = '';
            }

            if (nameUser.value == "" || (nameUser.value.length <= 3)) {
               Nom.value = "Le nom doit contenir au moins 4 caractères et uniquement alphabétique";
                //name.focus();
                return false;
            } else {
                Nom.value = "";
            }

            if (mailUser.value == "" || (mailUser.value.indexOf("@", 0) < 0) || (mailUser.value.indexOf(".", 0) < 0)) {
                femail.value = "Mettez une adresse email valide.";
                //email.focus();
                return false;
            } else {
               femail.value = "";
            }

            if (dateUser.value == "") {
                fDtn.value= "Choisissez votre année de naissance.";
                //Dtn.focus();
                return false;
            } else {
                var udt= new Date(""+dateUser.value+"");
                var uyr= udt.getFullYear();
                var Ag = yr - uyr ;
            
                if(Ag < 16){
                    fDtn.value = "Vous devez avoir au moins 16 ans pour vous inscrires sur GameOn.";
                    //Dtn.focus();
                    return false;
                }else{
                    fDtn.value = "";
                }
            
            }

            if (nbgameUser.value == "" || isNaN(nbgameUser.value)) {
                fCmb.value = "Mettez un nombre.";
                //Cmb.focus();
                return false;
            } else {
                fCmb.value = "";
            }
           console.log('checkedA.value', checkedA.value);
            if(checkedA.value === 'yes'){
                fCheckA.value = '';
            }else{
                fCheckA.value = "Veuillez accepter nos conditions d'utilisations pour procéder à l'enregistrement";
            }

            formsuccess()


        }

        let formsuccess = function(){
            if (lastnameUser.value == "" || (nameUser.value == "") || (mailUser.value == "") || (dateUser.value == "")
                 || (nbgameUser.value == "")|| ((checkedA.value =='no') || (checkedA.value ==''))) {
                    resultForm.value = 0;
                    return false;
            } else {
                resultForm.value = 1;
                psucces.value = "Merci pour votre inscription";
                return true;
            }
        }

        let FermeModal = function(){
            Modalbox.value = 1;
            var lk = window.location.href;
             window.location.href = "" + lk + "";
        }

     
        return{
            lastnameUser,
            nameUser,
            mailUser,
            dateUser,
            nbgameUser,
            checkedA,
            fNom,
            Nom,
            femail,
            fDtn,
            yr,
            fCmb,
            fCheckA,
            resultForm,
            psucces,
            Modalbox,
            radios,

            validateForm,
            formsuccess,
            FermeModal,
        }
    }

}
</script>

<style lang="scss" scoped>
    #exampleModalLong{
        background-color:transparent;
        overflow: auto;
    
    }
    input[type=text], select, textarea {
    width: 100%;
    padding: 12px; 
    border: 1px solid #ccc; 
    border-radius: 5px; 
    box-sizing: border-box; 
    margin-top: 6px; 
  
    resize: vertical ;
}
input[type=date]{
    width: 100%;
    padding: 12px; 
    border: 1px solid #ccc; 
    border-radius: 5px; 
    box-sizing: border-box; 
    margin-top: 6px; 
  
    resize: vertical ;
}

input[type=email]{
  width: 100%;
  padding: 12px; 
  border: 1px solid #ccc; 
  border-radius: 5px; 
  box-sizing: border-box; 
  margin-top: 6px; 

  resize: vertical ;
}
input[type=number]{
  width: 100%;
  padding: 12px; 
  border: 1px solid #ccc; 
  border-radius: 5px; 
  box-sizing: border-box; 
  margin-top: 6px; 

  resize: vertical ;
}

input[type=submit] {
	margin-left:auto;
	margin-right:auto;
    background-color: #4CAF50;
    color: white;
    padding: 12px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}


input[type=submit]:hover {
    background-color: #45a049;
}
#psucces{
	font-size:2em;
	text-align: center;
    margin-top: 150px;
    margin-bottom: 150px;
}

.falseM{
	margin-top:0px;
	font-size:0.9em;
	color:red;
	
}
.btnModF{
    display: flex;
    align-content: center;
    justify-content: center;
    margin-bottom: 10px;
}
.radiob{
    display: inline-block;
    justify-items: flex-start;
    justify-self: self-start;
    margin-right: 20px;
    margin-bottom: 10px;
    input{
        vertical-align: middle;
        
    }
    span{
        margin-right: 1px;
    }
    
}

@media screen and (max-width: 540px) {

    .radiob{
        display: flex;
        margin-bottom: 10px;
        input{
            
            vertical-align: middle;
            
        }
       
    
    }


}
</style>