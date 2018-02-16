<template>
    <div class="test">
        <h1>{{title}}</h1>
        <input type="text" v-model="title"/><br/>
        <p v-if="showMe">{{user.firstName}}</p>
        <p v-else>Nobody</p>        
        
        <ul>
            <li v-for="item in items">{{item.title}}</li>
        </ul>
        
        <button v-on:click="great(title)">Stay greeting</button>
        <br/>
        <input type="text" v-on:keyup="keyPress" v-on:keyup.enter="hitEnter"/>
        
        <hr/>
        <label >First name</label><input type="text" v-model="user.firstName">
        <br/>
        <label >Last name</label><input type="text" v-model="user.lastName">
        <br/>
        <h3>{{fullname}}</h3>
        <h2>{{msg}}</h2>
    </div>
</template>

<script>
    export default{
        name: 'test',
        props: {
            msg: {
                default: "Foo",
                type:String
            }
        },
        data(){
            return {
                title:"Hello World",
                user:{
                    firstName: "John",
                    lastName: "Doe"
                },
                showMe:false,
                items:[
                    {title:"item1"},
                    {title:"item2"},
                    {title:"item3"}
                ]
            }
        },
        methods:{
            great:function(msg){
                alert(msg);
            },
            keyPress:function(e){
                console.log(e.target.value);
            },
            hitEnter:function(){
                alert("You hit enter");
            }
            
        },
        computed:{
            fullname: function(){
                return this.user.firstName + " "+this.user.lastName;
            }
        }
    }
</script>

<style scoped>

</style>