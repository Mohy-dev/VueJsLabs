<template>
<div class="container">
 <form v-if="showMain" @submit="checkForm" class="row g-3 needs-validation" novalidate>
   <div>
  <div class="col-md-4 position-relative">
    <label for="validationTooltip01" class="form-label">First name</label>
    <input v-model="fname" type="text" class="form-control" id="validationTooltip01" required>
    <div class="valid-tooltip">
      Looks good!
    </div>
    <div class="invalid-tooltip">
        Fill it please
    </div>
  </div>
<div class="col-md-4 position-relative">
    <label for="validationTooltip01" class="form-label">Last name</label>
    <input v-model="lname" type="text" class="form-control" id="validationTooltip01" required>
    <div class="valid-tooltip">
      Looks good!
    </div>
    <div class="invalid-tooltip">
        Fill it please
    </div>
  </div>
  <div class="col-md-4 position-relative">
    <label for="validationTooltip01" class="form-label">Age</label>
    <input v-model="age" type="text" class="form-control" id="validationTooltip01" required>
    <div class="valid-tooltip">
      Looks good!
    </div>
    <div class="invalid-tooltip">
        Fill it please
    </div>
    <div v-for="error in errors" :key="error">
      {{error}}
    </div>
  </div>
  <div class="col-md-4 position-relative">
    <label for="validationTooltip01" class="form-label">Email</label>
    <input v-model="email" type="email" class="form-control" id="validationTooltip01" required>
    <div class="valid-tooltip">
      Looks good!
    </div>
    <div class="invalid-tooltip">
        Fill it please
    </div>
  </div>
  <div class="col-12 mt-3">  
    <button class="btn btn-primary col-12" type="submit" @click="showData=true, showMain=false">Confirm Info</button>
  </div>
  </div>
</form>
<div id="showData" v-if="showData">
  <label for="nameInfo">Your First Name: &nbsp;</label>
  <span id="nameInfo" class="text-muted">{{fname}}</span><br>
   <label for="nameInfo">Your Last Name: &nbsp;</label>
  <span id="nameInfo" class="text-muted">{{lname}}</span><br>
   <label for="nameInfo">Your Email: &nbsp;</label>
  <span id="nameInfo" class="text-muted">{{email}}</span><br>
   <label for="nameInfo">Your Age: &nbsp;</label>
  <span id="nameInfo" class="text-muted">{{age}}</span><br>
  <div class="d-flex justify-content-around">
  <button class="btn btn-primary alig m-3" @click="sure">Submit</button>
  <button class="btn btn-warning m-3" @click="showMain=true, showData=false">Back</button>
  </div>
</div>
<div id="submmited" v-if="submited">
  <h3 class="text-center text-primary">Thank you your data submitted successfully</h3>
  <img class="animated-gif rounded mx-auto d-block" src="../assets/11.gif" alt="Loading">
  <h3 class="text-center text-primary">Get you back in a moment</h3>
</div>
</div>
</template>

<script>
export default {
  data() {
    return{
      fname:"",
      lname:"",
      email:"",
      age:"",
      showMain:true,
      showData:false,
      submited:false,
      myTimeout:null,
      errors: []
    } 
  },
  methods:{
    checkForm : function(e){
      if (isNan(this.age)) {     
        this.errors = [];
        this.errors.push('Age required as a number');
        e.preventDefault();
      }
    },
    backToMain(){
      this.showMain= true;
      this.submited = false;
      clearTimeout(this.myTimeout);
    },
    sure()
    {
      if( confirm("Are you sure about this data, process to submit it")){
        this.submited = 1;
        this.showData = 0;
        this.fname = null;
        this.lname = null,
        this.email = null,
        this.age = null,
        this.myTimeout = setTimeout(this.backToMain, 4000);
      }
    },
  },
}
</script>


<style scoped>
  template{
    height: 77vh;
  }
  #showData{
     margin-top: 3rem;
    height: 70vh;
  }
  img.animated-gif{
  margin: 1px auto;
  width: 200px;
  height: 200px;
  }
  #submmited{
    margin-top: 3rem;
    height: 70vh;
  }
  form{
    height: 77vh;
  }
  .form.div{
    margin-top:3rem;
  }
</style>