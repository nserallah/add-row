<template>
    <div> 
        <div class="container">
            <h1>Family Information:</h1>
            <table>
                <thead>
                    <td><h4>Remove One</h4></td>
                    <td>
                        <h4>Full Name</h4>
                    </td>
                    <td>
                        <h4>Dirthday</h4>
                    </td>
                    <td>
                        <h4>Age</h4>
                    </td>
                    <td>
                        <h4>Sex</h4>
                    </td>
                </thead>
                <tr v-for="(familyMemder, k) in familyMemders" :key="k">
                    <td scope="row" class="trashIconContainer">
                        <i class="far fa-trash-alt" @click="deleteRow(k, familyMemder)"></i>
                    </td>
                    <td>
                        <input class="form-control" type="text" v-model="familyMemder.Name" />
                    </td>
                    <td>
                        <form>
                            <input class="form-control" type="date" name="birthday" v-model="familyMemder.birthDay">
                        </form>
                    </td>
                    <td>
                        <input class="form-control text-right" type="number" min="0" step=".01" v-model="familyMemder.age" />
                    </td>
                    <td>
                        <form>
                        <div class="pretty p-default p-curve">
                            <input type="radio" value="male" v-model="familyMemder.sex" name="sex" />
                            <div class="state p-primary-o">
                                <label>Male</label>
                            </div>
                        </div>

                        <div class="pretty p-default p-curve">
                            <input type="radio" value="female" v-model="familyMemder.sex" name="sex" />
                            <div class="state p-success-o">
                                <label>Female</label>
                            </div>
                        </div>
                        </form>
                    </td>
                </tr>
            </table>
            
            <div class="row">
                <div class="col text-left button-add">
                    <button type='button' class="btn btn-info mt-2" @click="addNewRow">
                        <i class="fas fa-plus-circle"></i>
                        Add
                    </button>
                </div>
                <div class="col text-right member-count">
                    <p class="lead bg-primary text-white">{{familyMemders.length}} Member</p>
                </div>
            </div>
            
        </div>
        
    </div>
</template>

<script>

export default {
    name: "addRow",
    data: function() {
        return {
            familyMemders: [{
            Name: '',
            birthDay: '',
            age: '',
            sex: '',  
        }]
         
        }
    },
    methods: {
        addNewRow() {
        
            this.familyMemders.push({
            Name: '',
            birthDay: '',
            age: '',
            sex: '', 
        });
            
        },
        deleteRow(index) {
            if (index > 0) {
                this.familyMemders.splice(index, 1);
            }
        },
    }
    
}


</script>

<style scoped lang="scss">
    table {margin:auto; width: 100%}

    table thead td{
        background: #e8e9ee;
    }

    table thead td, tr td {
        padding: 10px;
        border: 1px solid #333
    }

    .trashIconContainer i {
        cursor: pointer;
        color: #007bff;
    }
    .member-count p{
        display: inline-block;
        padding: 10px 30px
    }

    .button-add button {
        padding: 10px 40px;

    } 
   
    

</style>