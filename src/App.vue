<script>
export default {
  data() {
    return {
      title: 'My New Vue Title',
      message: 'Welcome to Vue',
      textStatus: {
        isRed: true,
      },
      users: [
        {
          firstName: 'Taro',
          lastName: 'Yamada',
          isMember: true,
        },
        {
          firstName: 'Tanaka',
          lastName: 'Yamada',
          isMember: false,
        },
        {
          firstName: 'Tabuchi',
          lastName: 'Yamada',
          isMember: true,
        },
      ],
    }
  },
  computed: {
    fullName() {
      return this.user.firstName + ' ' + this.user.lastName
    },
  },
}
</script>

<template>
  <h1 v-bind:title="message" v-bind:class="textStatus">
    {{ title }}
  </h1>
  <h2>ユーザーのデータ</h2>
  <div v-for="user in users">
    <p>Name: {{ user.firstName + ' ' + user.lastName }}</p>
    <p v-if="user.isMember">メンバーです</p>
    <p v-else>メンバーではありません</p>
  </div>
</template>

<style>
.red {
  color: red;
}
</style>
