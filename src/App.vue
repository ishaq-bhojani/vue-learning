<template>
  <h2>Friends List</h2>
  <Form @add-friend="onAddFriend" />
  <ul>
    <Friend
    v-for="friend in friends"
    :key="friend.id"
    :id="friend.id"
    :name="friend.name"
    :email="friend.email"
    :phone="friend.phone"
    :is-favourite="friend.isFavourite"
    @on-favourite="onFavourite" />
  </ul>
</template>

<script>
import Friend from './components/Friend-Comp.vue';
import Form from './components/Friend-Form.vue';

export default {
  name: 'App',
  components: {
    Friend,
    Form
  },
  data () {
    return {
      friends: [
                {
                  id: '1',
                  name: "Ishaq",
                  phone: "+923214567890",
                  email: "ishaqbhojani@gmail.com",
                  isFavourite: true
                },
                {
                  id: '2',
                  name: "Nadir",
                  phone: "+92321434550",
                  email: "nadir11@gmail.com",
                }
      ]
    }
  },
  methods: {
    onFavourite(friendId) {
      const friendFound = this.friends.find(friend => friend.id === friendId);
      friendFound.isFavourite = !friendFound.isFavourite;
    },
    onAddFriend(data) {
      this.friends.push({
        id: String(this.friends.length + 1),
        ...data
      })
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
ul li {
  list-style: none;
  margin: 20px;
}
</style>
