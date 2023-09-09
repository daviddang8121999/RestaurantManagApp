<template>
<h1>Sign Up</h1>
<div class="register">
    <input type="text" v-model="name" placeholder="Please enter Name" />
    <input type="text" v-model="email" placeholder="Please enter Email" />
    <input type="password" v-model="password"  placeholder="Please enter Password" />
    <button v-on:click="signUp" >Sign Up</button>
</div>
</template>
<script>
import axios from 'axios'
export default {
    name:'SignUp',
    data()
    {
        return{
            name:'',
            email:'',
            password:''
        }
    },
    methods:{
        async signUp()
        {
            let result = await axios.post("http://localhost:3000/users",{
                email:this.email,
                password:this.password,
                name:this.name
            });

            console.warn(result);
            if(result.status==201)
            {
                alert("sign-up done");
                localStorage.setItem("user-info",JSON.stringify(result.data))
            }
        }
    }
}
</script>

<style>
.register input{
    width: 300px;
    height: 40px;
    display: block;
    padding-left: 20px;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 2px solid green;
}
.register button{
    width: 320px;
    height: 40px;
    border: 1px solid green;
    background: green;
    color: white;
    cursor: pointer;
    
}

</style>
