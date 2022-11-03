<template>
  <v-container>
    <v-row no-gutters>
      <v-col class="credit">

        <v-col>
          <v-img src="../images/bg-card-front.png" width="400px"  class="credit ma-2">
            <v-row> <div class="ball"></div> <div class="bell"></div></v-row>
            
            <div class="number"><p>{{number}}</p></div>

            <div class="lowData">
              <v-row>
                <v-col  md="9">  
                  <span style="text-transform: uppercase;">{{name}} </span>
                </v-col>
                
                <v-col >
                  <span> {{mm}}/{{yy}}</span>
                </v-col>
              </v-row>
            </div>

          </v-img>
       </v-col>
      
        <v-col class="back">
          <v-img src="../images/bg-card-back.png" width="400px" class="credit ma-2">
            <p class="cvc">{{cvc}}</p>
          </v-img>
        </v-col>
      </v-col>
    
      <v-col md="4" class="dados">

    <v-stepper v-model="e1" elevation="0">

      <v-stepper-items>
        <v-stepper-content step="1">


      <span class="dataSpan">CARDHOLDER NAME</span>
        <v-text-field
        outlined dense required
        :rules="rules"
        placeholder="Your Name"
        v-model="newName" @input="changeName()" 
        color="purple darken-2"
        ></v-text-field>
        
        <span class="dataSpan">CARD NUMBER</span>
        <v-text-field 
        outlined dense 
        :rules="rules"
        placeholder="0000 0000 0000 0000"
        color="purple darken-2"
        v-mask="'#### #### #### ####'" v-model="newNumber" @input="changeNumber()"
        ></v-text-field>
        
        <v-row>
          <v-col
           md="6" class="dataSpan">
          <span>EXP. DATE (MM/YY)</span>
          </v-col>

          <v-col
           md="6" class="dataSpan">
            <span>CVC</span>
          </v-col>

          <v-col 
            md="3">
            <v-text-field
            placeholder="MM" outlined dense v-model="newMm" v-mask="'##'" @input="changeMm()"
            color="purple darken-2"
            ></v-text-field>
          </v-col>
          
          <v-col
            md="3">
            <v-text-field 
            placeholder="YY" outlined dense v-model="newYy" v-mask="'##'" @input="changeYy()"
            color="purple darken-2"
            ></v-text-field>
          </v-col>
          
          <v-col
            md="6">
            <v-text-field 
            placeholder="e.g. 123" required
            outlined dense 
            v-model="newCvc" v-mask="'###'" @input="changeCvc()"
            color="purple darken-2"
            ></v-text-field>
          </v-col>
        </v-row>

        <v-btn color="hsl(278, 68%, 11%)" @click="checkData()"
        style="color:white;height: 50px; border-radius: 10px;" block>Confirm</v-btn>


        </v-stepper-content>

        <v-stepper-content step="2">
          <div class="confirm">
             <v-icon class="ballPurple"
               large
               color="white"
             >
               mdi-check
             </v-icon>  
            <h1>THANK YOU!</h1>
            <p>We've added your card details</p>
            
            <v-btn color="hsl(278, 68%, 11%)" @click="e1=1"
            style="color:white;height: 50px; border-radius: 10px;" block
            >
            Continue
          </v-btn>
        </div>

        </v-stepper-content>

      </v-stepper-items>
    </v-stepper>
  
      </v-col>

    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'clonas',
    data(){
      return{
        e1: '1',
        number: '0000 0000 0000 0000',
        newNumber: '',
        name: 'Your Name  ',
        newName: '',
        mm: '00',
        newMm: '',
        yy: '00',
        newYy: '',
        cvc: '000 ',
        newCvc: '',
        rules: [
          value => !!value || 'Required.',
        ],
      };
    },
    methods: {
      changeName(){
        if(this.newName != ''){
          this.name = this.newName
        }
        else{
          this.name = "Your Name"
        }
      },
      changeNumber(){
        if(this.newNumber != ''){
          this.number = this.newNumber
        }
        else{
          this.number = "0000 0000 0000 0000"
        }
      },
      changeMm(){
        if(this.newMm != ''){
          this.mm = this.newMm
        }
        else{
          this.mm = "00"
        }
      },
      changeYy(){
        if(this.newYy != ''){
          this.yy = this.newYy
        }
        else{
          this.yy = "00"
        }
      },
      changeCvc(){
        if(this.newCvc != ''){
          this.cvc = this.newCvc
        }
        else{
          this.cvc = "000"
        }
      },
      checkData(){
        if(this.newName && this.newNumber && this.newMm && this.newYy && this.newCvc != ''){
          this.e1=2
        }
      }
    }
  }
</script>

<style>
@media only screen and (max-width: 450px) { 
.ball{
  background-color: white;
  width: 35px;
  height: 35px;
  border-radius: 100%;
  margin:30px;
}
.bell{
  width: 15px;
  height: 15px;
  border: solid white 1px;
  border-radius: 100%;
  margin: 40px;
  margin-left: -10px;
}
.credit{
  color: white !important;
}
.back{
}
.cvc{
  margin-top: 77px; 
  margin-left: 260px; 
  font-weight: bold;
  letter-spacing: 2px;
}
.number{
  font-size: 20px;
  margin-top: 25px;
  margin-left: 30px;
  letter-spacing: 3px;
}
.lowData{
  font-size: 12px !important;
  letter-spacing: 2px;
  margin-left: 30px;
}
.dataSpan{
  font-size: 12px;
  margin-bottom: -14px;
  color: hsl(278, 68%, 11%);
  font-weight: bold;
}
.ballPurple{
  height: 70px;
  width: 70px;
  border-radius: 100%;
  background: linear-gradient(180deg, hsl(249, 99%, 64%) 0%,hsl(278, 94%, 30%) 100%);
}
.confirm{
  justify-content: center;
  justify-items: center;
  text-align: center;
}

}
@media only screen and (min-width: 500px) {
.ball{
  background-color: white;
  width: 40px;
  height: 40px;
  border-radius: 100%;
  margin:30px;
}
.bell{
  width: 20px;
  height: 20px;
  border: solid white 1px;
  border-radius: 100%;
  margin: 40px;
  margin-left: -10px;
}
.credit{
  margin-top: 70px;
  margin-left: 70px;
  color: white !important;
}
.back{
  margin-left: 90px;
}
.cvc{
  margin-top: 97px; 
  margin-left: 325px; 
  font-weight: bold;
  letter-spacing: 2px;
}
.number{
  font-size: 25px;
  margin-top: 55px;
  margin-left: 30px;
  letter-spacing: 3px;
}
.dados{
  margin-top: 170px !important;
}
.lowData{
  font-size: 12px !important;
  letter-spacing: 2px;
  margin-left: 30px;
}
.dataSpan{
  font-size: 12px;
  margin-bottom: -14px;
  color: hsl(278, 68%, 11%);
  font-weight: bold;
}
.ballPurple{
  height: 70px;
  width: 70px;
  border-radius: 100%;
  background: linear-gradient(180deg, hsl(249, 99%, 64%) 0%,hsl(278, 94%, 30%) 100%);
}
.confirm{
  justify-content: center;
  justify-items: center;
  text-align: center;
}

}
</style>