<template>
<div class="container">
 <form v-if="showMain" class="row g-3 needs-validation" novalidate>
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
  </div>
  <div class="col-md-12 position-relative">
    <label for="validationTooltip01" class="form-label">Email</label>
    <input v-model="email" type="email" class="form-control" id="validationTooltip01" required>
    <div class="valid-tooltip">
      Looks good!
    </div>
    <div class="invalid-tooltip">
        Fill it please
    </div>
  </div>
  <div class="col-12">  
    <button class="btn btn-primary col-12" type="submit" @click="showData=true, showMain=false">Confirm Info</button>
  </div>
</form>
<div v-if="showData">
  <label for="nameInfo">Your Name</label>
  <!-- <P id="nameInfo" v-model="fname"></P> -->
  <button class="btn btn-primary" @click="sure">Submit</button>
  <button class="btn btn-warning" @click="showMain``=true, showData=false">Back</button>
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
      age:null,
      showMain:true,
      showData:false,
      submited:false,
      myTimeout:null
    } 
  },
  methods:{
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
        this.myTimeout = setTimeout(this.backToMain, 5000);
      }
    },
  },
}
</script>


<style scoped>
  template{
    height: 77vh;
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
</style>