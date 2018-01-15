<template>
  <div class="test">
    <h1>{{title}}</h1>
    <input type="text" v-model="title" /><br />
    {{title}}

    <p v-if="showName">
       {{user.firstName}}{{user.lastname}}
    </p>
    <p v-else="showName">
       Nobody
    </p>

    <ul>
      <li v-for="item in items">
        {{item.title}}
      </li>
    </ul>

    <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit"/>
    <hr />

    <label>First name </label><input type="text" v-model="user.firstName" />

    <br  />

    <label>Last name </label><input type="text" v-model="user.lastName" />

    <br  />

    {{fullName}}

    <hr />
    {{msg}}

    <button v-on:click="greet('HelloWorld')">Say gretting</button>
  </div>
</template>


<script>
  export default {
    name: 'test',
    props: {
      msg:{
        type: String,
        default:'Foobar'
      }
    },
    data() {
      return {
        title: 'HelloWorld',
        user:{
          firstName: "john",
          lastName: "Doe"
        },
        "showName": false,
        items:[
          {title:"item one"},
          {title:"item two"},
          {title:"item three"}
        ]
      }
    },
    methods:{
      greet: function(greeting){
        alert(greeting)
      },
      pressKey: function(e){
          console.log(e.target.value)
      },
      enterHit: function(){
        console.log("you hit enter");
      }
    },
    computed: {
      fullName:function(){
        return this.user.firstName+ ' ' + this.user.lastName
      }
    }
  }
</script>
