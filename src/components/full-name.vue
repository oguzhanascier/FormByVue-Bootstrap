<template>
    <div>
      
        <!-- / A form input for firstname. -->
        <div class="mb-3">
            <label class="form-label">
                Firstname
            </label>
        
            <input type="text" class="form-control"   :value="firstName" @input="nameChanged(true, $event)" >
        </div>
        
        <!-- /A form input for lastname. -->
        <div class="mb-3">
            <label  class="form-label">
                Lastname
            </label>
            <input class="form-control"  :value="lastName" @input="nameChanged(false, $event)">
        </div>
  
    </div>
</template>
<script>
export default{
 props: ["value"],

 computed:{
    firstName(){
            return this.value.split(" ")[0];
        },
    lastName(){
            return this.value.split(" ")[1]

        },
    },
 methods:{
    nameChanged(isFirst, event){
      
        let fullName="";
            if(isFirst){
                fullName =event.target.value+ " "+this.lastName
            }else{
                fullName = this.firstName + " " +event.target.value 
            }
            this.value=fullName
            this.$emit('input',this.value)
    }
 }
}
</script>
