<template>
  <vs-row vs-justify="center">
    <vs-col type="flex" vs-justify="center" vs-align="center" vs-lg="3" vs-sm="6" vs-xs="10">
      <vs-card actionable>
        <div slot="header">
          <h3>Welcome our guest</h3>
        </div>
        <div class="centerx">
          <vs-row vs-justify="center">
            <vs-input size="large" 
            label-placeholder="Checkin Date" v-model="checkin" type="date"/><br>
              <span v-if="msg.checkiin">{{msg.checkin}}</span>
              <br>
            <vs-input size="large" label-placeholder="Checkout Date"
             v-model="checkout" type="date"/><br>
              <span v-if="msg.checkout">{{msg.checkout}}</span>
              <br>
            <vs-input size="large" label-placeholder="Your Name"
             v-model="username" type="text"/>              
              <span v-if="msg.username">{{msg.username}}</span>
              <br>
            <vs-input size="large" 
            label-placeholder="Email" v-model="email" type="email"/>
            <br>
              <span v-if="msg.email">{{msg.email}}</span>
              <br>            
          </vs-row>
        </div>
        <div slot="footer">
          <vs-row vs-justify="flex-end">
            <vs-button size="large" type="gradient" color="primary">Place Booking</vs-button>
          </vs-row>
        </div>
      </vs-card>
    </vs-col>
  </vs-row>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      username: ",",
      email: "",
      checkin : "",
      checkout : "",
      msg: [],
    };
  }, watch: {
    email(value){
      // binding this to the data value in the email input
      this.email = value;
      this.validateEmail(value);
    },
    username(value){
      this.username = value;
      this.validateUsername(value);
    }
  },
  methods:{
    validateEmail(value){
      if (/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(value))
        {
            this.msg['email'] = '';
        } else{
            this.msg['email'] = 'Invalid Email Address';
        } 
    },validateUsername(value){
      if (value.length == 0) {
        this.msg['username'] = 'Username required' ;
      } else {
         this.msg['username'] = '';
      }
    }
  }
}
</script>
<style>
body {
  min-height: 100vh;
  background-image: radial-gradient(
    circle 621px at 25.3% 13.8%,
    rgba(255, 255, 255, 1) 0%,
    rgba(234, 236, 255, 1) 90%
  );
  margin-top: 50px;
  font-family: "Roboto", sans-serif;
}
</style>
