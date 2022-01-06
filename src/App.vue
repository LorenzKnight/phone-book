<template>
  <div id="app">
    <div class="container">
      <div class="sidebar">
        <p><strong>Add a new contact:</strong></p>
          <form @submit.prevent="addUser">
            <label>First Name: <input type="text" v-model="name" class="userFirstname" /></label> <br />
            <label>Last Name: <input type="text" v-model="surname" class="userLastname" /></label> <br />
            <label>Phone: <input type="number" v-model="phone" class="userPhone" /></label> <br />
            <button type="submit" class="submitButton" @mouseout="sortBy">Add New Contact</button>
          </form>
      </div>
      <div class="content">
        <table width="95%">
          <tr height="40" style="color: #000; font-weight: 600;">
            <td width="40%">Name</td>
            <td width="40%">Surname</td>
            <td width="20%">Phone</td>
          </tr>
          <tr v-for="user in users" v-bind:key="user.surname">
            <td>{{user.name}}</td>
            <td>{{user.surname}}</td>
            <td>{{user.phone}}</td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "App",
    data() {
      return {
        name: 'Coder',
        surname: 'Byte',
        phone: '8885559999',
        users: []
      }
    },
    methods: {
      addUser()
      {
        var data = {
          name: this.name,
          surname: this.surname,
          phone: this.phone
        };
        this.users.push(data);
        this.name = '';
        this.surname = '';
        this.phone = '';
      },
      sortBy: function() {
        console.log('rearrange');
        this.users.sort((a,b) => a['surname'] < b['surname'] ? -1 : 1)
      }
    }
    
  };
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
}
#app {
  width: 100%;
  height: 100vh;
  background-color: #F0F0F0;
  color: #2c3e50;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  justify-content: center;
  align-items: center;
}
.container {
  width: 800px;
  height: 600px;
  background-color: white;
  border-radius: 7px;
  padding: 10px;
  display: flex;
  box-shadow: 0px 0px 15px 0px rgba(0,0,0,0.1);
}
.sidebar {
  width: 200px;
  padding: 0 30px;
  text-align: center;
  border-right: 1px solid #CCC;
}
.content {
  flex: 1;
}
input {
  margin: 5px;
  padding: 5px;
  border-radius: 4px;
  border: 1px solid #CCC;
  text-align: center;
}
button {
  margin: 15px;
  padding: 10px 25px;
  background: olivedrab;
  color: white;
  border: none;
  border-radius: 4px;
}
table {
  margin: 0 auto;
}
</style>
