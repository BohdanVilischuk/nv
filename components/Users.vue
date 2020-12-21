<template>
  <div>
    <form action="">
      <div>
        ava
        <input v-model="addUser.avatar" type="text" />
      </div>
      <div>
        firstN
        <input v-model="addUser.firstName" type="text" />
      </div>
      <div>
        lastN
        <input v-model="addUser.lastName" type="text" />
      </div>
      <div>
        job title
        <input v-model="addUser.title" type="text" />
      </div>
      <div>
        date
        <input v-model="addUser.date" type="text" />
      </div>
      <div>
        phone
        <input v-model="addUser.phone" type="text" />
      </div>
      <div>
        email
        <input v-model="addUser.email" type="text" />
      </div>
      <div>
        bio
        <input v-model="addUser.biography" type="text" />
      </div>

    </form>
    <button  v-if="savebtn" @click.prevent="save">
      Add
    </button>
    <button v-if="updatebtn" @click.prevent="update(addUser.avatar)">
      Update
    </button>
    <button @click.prevent="clear">
      Unset
    </button>
    <div class="users" v-for="(user, index) in users" v-bind:key="index">
      <div class="user">
        <div>
          {{ user.avatar }}
        </div>
        <div>
          {{ user.firstName }}
        </div>
        <div>
          {{ user.lastName }}
        </div>
        <div>
          {{ user.firstName }}
        </div>
        <div>
          {{ user.phone }}
        </div>
        <div>
          {{ user.email }}
        </div>
        <div>
          {{ user.biography }}
        </div>
        <div class="buttons">
          <button @click="edit(user)" >
            Edit
          </button>
          <button @click="remove(user)">
            Remove
          </button>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
 export default {
   data: function () {
     return {
       users: [
         { avatar: 'ava1', firstName: 'John', lastName: 'Doe', title: "PM", date : '2012', phone: '+33003302321', email: 'test@mail.com', biography: 'Text TextTextTextTextText TextTextText TextTextText' },
         { avatar: 'ava2', firstName: 'Joh1', lastName: 'Do1', title: "AM", date: '2013', phone: '+33003302325', email: 'test1@mail.com', biography: 'Text TextTextTextTextText TextTextText TextTextText' },
         { avatar: 'ava3', firstName: 'Joh2', lastName: 'Do2', title: "RM", date: '2015', phone: '+330033023266', email: 'test2@mail.com', biography: 'Text TextTextTextTextText TextTextText TextTextText' }
       ],
       addUser: {
         avatar: '',
         firstName: '',
         lastName: '',
         title: '',
         date: '',
         phone: '',
         email: '',
         biography: ''
       },
       savebtn: true,
       updatebtn: false
     }
   },
   methods: {
     save: function () {
       let ava = this.addUser.avatar
       let fn = this.addUser.firstName
       let ln = this.addUser.lastName
       let ttl = this.addUser.title
       let dt = this.addUser.date
       let ph = this.addUser.phone
       let em = this.addUser.email
       let bio = this.addUser.biography

       this.users.push({avatar: ava, firstName: fn, lastName: ln, title: ttl, date: dt, phone: ph, email: em, biography: bio})
       this.clear()
       swal('Added', 'Data', 'success')
     },
     clear: function () {
       this.savebtn = true
       this.updatebtn = false
       this.addUser.avatar = ''
       this.addUser.firstName = ''
       this.addUser.lastName = ''
       this.addUser.title = ''
       this.addUser.date = ''
       this.addUser.phone = ''
       this.addUser.email = ''
       this.addUser.biography = ''
     },
     
   }
 }
</script>

<style>
.users {
  justify-content: space-between;
  flex-wrap: wrap;
  display: flex;
}
.user {
  flex: 1;
  margin: 2em;
  border: 1px solid #000;
  padding: 20px;
  display: flex;

}
.user div {
  margin: 10px;
}

</style>
