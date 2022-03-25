<template>
    <table class="table table-striped table-bordered text-center">
        <thead>
            <tr>
                <th>ID</th>
                <th>Name</th>
                <th>City</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="one in data" :key="one.id">
                <td>{{one.id}}</td>
                <td>{{one.name}}</td>
                <td>{{one.city}}</td>
            </tr>
        </tbody>
        <tfoot>
            <th colspan="3" class="mt-1">Total Number is of entries {{data.length}}</th>
        </tfoot>
    </table>
    <button class="btn btn-success mt-1 col-12" data-bs-target="#addNewEntery" data-bs-toggle="modal">Add</button>
    <div class="modal fade" id="addNewEntery">
        <div class="modal-dialog modal-dialog-centered" data-bs-keyboard="false" data-bs-backdrop="static">
            <div class="modal-content">
                <div class="modal-header">
                    <h4>Add New Person</h4>
                </div>
                <div class="modal-body">
                    <form>
                        <input v-model="pname" type="text" class="form-control my-2" placeholder="Name" >
                        <p v-if="notOK == 1" class="text-danger mr-1">Characters are only allowed</p>
                        <input v-model="pcity" type="text" class="form-control my-2" placeholder="City" >
                    </form>
                </div>
                <div class="modal-footer">
                    <button @click="add" class="btn btn-success" data-bs-dismiss="modal" id="btn1">Add</button>
                    <button class="btn btn-danger" data-bs-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import data from '../ppl'
export default {
    data:()=> ({
        data:data,
        pname:"",
        pcity:"",
        id:10,
        notOK:0
    }),
    methods:{
    
        add(){
            let isOkName = /^[a-zA-Z ]+$/.test(this.name);
            if(!isOkName){
            this.data.push({id:this.data[this.data.length - 1].id + 1, name:this.pname, city:this.pcity});
            //address issue
            notOK = 0;
            }else{
                document.getElementById("btn1").addEventListener("click", function(event){
                event.preventDefault()
                });
                notOK = 1; // two way happens??
            }
        }
    }
}
</script>
