<template>
    <div class="container">
        <div class="row">
            <div class="alert alert-info">
                Our lift moves between floors in 5 seconds, please be patient
            </div>
        </div>
        <div class="row">
            <div class="col-md-4">
                <form>
                    <div class="row">
                        <div class="input-group col-md-12">
                            <input type="text" class="form-control" placeholder="Full Name" aria-describedby="basic-addon1" v-model="fullName">
                        </div>
                    </div>
                    <div class="row">
                        <div class="input-group col-md-12">
                            <select class="form-control" v-model="recipient">
                                <option>TO SEE WHOM?</option>
                                <option v-for="r in recipients" :value="r.floor">{{ r.name }}</option>
                            </select>
                        </div>
                    </div>
                    <div class="row">
                        <div class="input-group col-md-12">
                            <label>Purpose of Visit</label>
                            <textarea class="form-control" v-model="purpose"></textarea>
                        </div>
                    </div>
                    <div class="row">
                        <button type="button" class="btn btn-primary" v-on:click="submitRequest">Submit Request</button>
                    </div>
                </form>
            </div>
            <div class="col-md-3 col-md-offset-1">
                <div class="row">
                    <h3>Floor Number: {{ recipient }}</h3>
                    <div class="col-md-12">
                        <p>You are on floor:</p>
                        <h2 class="text-align: center">{{ floorNumber }}</h2>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'hello',
    data () {
        return {
            msg: 'Welcome to Your Vue.js App',
            recipients: [
                {name: 'Mr. Oshosanya Michael', floor: 5},
                {name: 'Mrs. Theresa May', floor : 3},
                {name: 'Mr. Kim Jong Un', floor : 2},
                {name: 'Mrs. Angela Merkel', floor : 6}
            ],
            floorNumber: 0,
            purpose: "",
            recipient: "",
            fullName: ""
        }
    },
    methods: {
        submitRequest: function()
        {
            var i = 0;
            var $this = this
            var recur = function() {  
                setTimeout(function()
                {
                    console.log($this.floorNumber)
                   $this.floorNumber+=1; 
                   if($this.floorNumber!=$this.recipient)
                    {
                        recur();
                    }
                    else
                    {
                        alert("You are at your destination, check with the receptionist")
                        $this.floorNumber = 0;
                        $this.purpose = "";
                        $this.recipient = "";
                        $this.fullName = "";
                    }
                }, 5000)
                //console.log($this.floorNumber)
                // if($this.floorNumber!=$this.recipient)
                // {
                //     recur();
                // }
            }
            recur();

            // for(i=0; i<this.recipient; i++)
            // {
            //     // this.floorNumber+=1; 
                
            // }
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
