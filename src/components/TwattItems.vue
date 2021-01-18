<template>
    <div class="twatt-item" @click="favoriteTwatt(twatt.id)">
        <div class="user-profile__twatt">
            <div class="twatt-item__user">
                @{{ username }}
            </div>
            <div class="twatt-item__content">
                {{ twatt.content }}
            </div>
        </div>
    </div>
</template>

<script>

export default {
  name: 'TwattsItems',
  props: {
    username: {
        type: String,
        required: true
    },
    twatt: {
        type: Object,
        required: true
    }
  },
  methods: {
      favoriteTwatt(id) {
          this.$emit('favorite', id);
      }
  }
}
</script>

<style>
   .twatt-item {
       padding: 1rem;
       background-color: white;
       border-radius: 5px;
       border: 1px solid #DFE3E8;
       box-sizing: border-box;
       cursor: pointer;
       transform: scale(0.9);
       transition: all 0.25s ease;
   }
   .twatt-item:hover{
       transform: scale(1);
   }
   .twatt-item__user {
       font-weight: bold;
   }
</style>
