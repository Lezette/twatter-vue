<template>
  <div class="user-profile">
     <div class="user-profile__user-panel">
         <h1 class="user-profile__username"> @{{user.username}}</h1>
         <div class="user-profile__admin" v-if="user.isAdmin">
             Admin
         </div>
         <div class="user-profile__follower-count">
            <strong>Followers</strong> {{ followers }}
      </div>
     </div>
     <div class="user-profile__twatts-wrapper">
         <TwattsItems v-for="twatt in user.twatts" :key="twatt.id" :username="user.username" :twatt="twatt" @favorite="toggleFavorite" />
     </div>
  </div>
</template>

<script>
import TwattsItems from './TwattItems';
export default {
  name: 'UserProfile',
  components: { TwattsItems },
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: 'ilizette',
        firstname: 'Elizabeth',
        lastname: 'Lola',
        isAdmin: true,
        twatts: [
            {id: 3, content: "Hey welcome to twatts"},
            {id: 6, content: "You're amazing and blessed"},
        ]
      }
    }
  },
  watch: {
    followers(newData, oldData) {
      if(oldData < newData) {
        console.log(`${this.user.firstname} gained a new follower`);
      }
    }
  },
  computed: {
    fullName() {
      return `${this.user.firstname} ${this.user.lastname}`;
    }
  },
  methods: {
    followUser() {
      this.followers++
    },
    toggleFavorite(id) {
        console.log(`favorite twatt ${id}`);
    }
  },
  mounted() {
    this.followUser();
  },
}
</script>

<style>
    .user-profile {
        display: grid;
        grid-template-columns: 1fr 3fr;
        overflow-x: hidden;
        padding: 50px 5%;
        margin: 0 1rem;
    }
    .user-profile__user-panel {
        display: flex;
        flex-direction: column;
        margin-right: 50px;
        padding: 20px;
        border-radius: 5px;
        border: 3px solid #DFE3E8;
    }
    h1 {
        margin: .5rem 0;
    }
    .user-profile__admin {
        background-color: rebeccapurple;
        color: white;
        margin: .5rem 0;
        margin-right: auto;
        border-radius: 5px;
        padding: .2rem;
    }
</style>
