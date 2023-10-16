<template>
    <div>
        <nav class="navbar navbar-expand navbar-light bg-light ">
            <div class="container-fluid" id="overlay">
                <div class="navbar-header">
                <button type="button" class="navbar-toggle" data-toggle="collapse" data-target="#myNavbar">
                    <span class="burger-icon">
                    <span></span>
                    <span></span>
                    <span></span>
                    </span>

                </button>

                <div class="header-logo">
                    <img alt="logo" src="@/assets/gamog.jpg" width="auto" height="auto" />
                </div>
                </div>
                <div class="collapse navbar-collapse" id="myNavbar">
                <ul class="nav navbar-nav navbar-right">
                    <li v-for="nav in MyNav" :key="nav"><a  :href="nav.url" class="{{role}}" @click=" activ() " >{{nav.name}}</a></li>
                    <!--li><a href="">A propos</a></li>
                    <li><a href="">Contact</a></li>
                    <li><a href="">Evènement passés</a></li-->
                </ul>
                </div>
            </div>
        </nav>


    </div>
</template>

<script >
import { ref } from 'vue';
export default {
    setup() {
        let role=ref ({
           act:'active',
        });
        let MyNav= [
            {name: 'Details de l\'évènement', role: role ,url:'#' },
            {name: 'A Propos', role:'',url:'#' },
            {name: 'Contact', role:'',url:'#' },
            {name: 'Evènement passés', role:'',url:'#' }
        ];

        let activ = function (){
            role.value = 'active';
            console.log('role || activ',role.value)
        }
        //console.log('MyNav',MyNav)
        console.log('role',role.value)
        console.log('roleT',(role.value= !role.value))
        return {
            
            MyNav,
            activ,
            role,
        }

    }
}
</script>

<style lang="scss">
    .navbar{
        overflow-x: hidden;
        background-color: #ffffff;
        padding-left: 30px;
        padding-right: 30px;
        margin-left: 0px;
        // border: 1px solid red;
        width: auto;

        .nav{
            a{
                font-size: 18px;
                color: rgba(0, 0, 0, 1);;

                &.active{
                    background-color: #fd0c2c;
                    color: rgba(255, 255, 255, 1);
                    text-decoration:underline;
                    border-radius: 5px;
                }

                &:hover{
                    background-color: #fd0c2c;
                    color: rgba(255, 255, 255, 1);
                    text-decoration:underline;
                    border-radius: 5px;
                    // margin: 0px 5px 0px 0px;
                }

            }

        }
    }

    .burger-icon span{
        display: block;
        border: none;
        width: 35px;
        height: 5px;
        background-color: black;
        margin: 6px 0;
        right: 0;
    }
</style>