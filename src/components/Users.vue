<template>
    <div class="users">
        <h1>Users</h1>
        
        <form v-on:submit="addUser">
            <input type="text" v-model="newUser.firstName" placeholder="first name"/>
            <input type="text" v-model="newUser.lasttName" placeholder="last name"/>
            <input type="text" v-model="newUser.email" placeholder="email"/>
            <input type="submit" value="submit"/>
        </form>
        

        <ul>
            <li v-for="user in users">
                <!--Add the class so if it's contacted, it;s gonna toggle the class-->

                <!--use span: to make the framework possible-->
                <span :class="{contacted:user.contacted}">
                    <button v-on:click="deleteUser(user)">Delete User</button>
                    {{user.firstName}} {{user.lastName}} {{user.email}}
                    <input type="checkbox" class="toggle" v-model="user.contacted"/>
                </span>

            </li>
        </ul>
    </div>
</template>

<script>
    export default{
        name: 'users',
        data(){
            return {
                newUser:{},
                users:[
                    {
                        firstName: "John",
                        lastName: "Doe",
                        email:"example@mail.com",
                        contacted:false
                    },
                    {
                        firstName: "Ben",
                        lastName: "Frank",
                        email:"bexample@mail.com",
                        contacted:false
                    },
                    {
                        firstName: "Casde",
                        lastName: "Fack",
                        email:"csle@mail.com",
                        contacted:false
                    }
                ]
            }
        },
        methods:{
            addUser:function(e){
                //stop doing the refershing
                e.preventDefault();
                this.users.push(
                    {
                        firstName: this.newUser.firstName,
                        lastName: this.newUser.lastName,
                        email: this.newUser.email,
                        contacted: false
                    });
            },
            
            deleteUser: function(user){
                this.users.splice(this.users.indexOf(user),1);
            }
            
            
        },
        computed:{

        }
    }
</script>

<style scoped>
    .contacted{
        text-decoration: line-through;
    }
</style>