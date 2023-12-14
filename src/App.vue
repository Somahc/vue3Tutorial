<script>
export default {
  data() {
    return {
      title: 'My New Vue Title',
      message: 'Welcome to Vue',
      textStatus: {
        isRed: true,
      },
      input: {
        firstName: '',
        lastName: '',
        isMember: true,
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
    isButtonDisabed() {
      return !this.input.firstName || !this.input.lastName
    },
  },
  methods: {
    addUser() {
      this.users.push(this.input)
      this.input = {
        firstName: '',
        lastName: '',
        isMember: true,
      }
    },
  },
}
</script>

<template>
  <h1 v-bind:title="message" v-bind:class="textStatus">
    {{ title }}
  </h1>
  <input type="text" v-model="input.firstName" />
  <input type="text" v-model="input.lastName" />
  <input type="checkbox" v-model="input.isMember" />
  <button @click="addUser" :disabled="isButtonDisabed">ユーザー追加</button>
  <h2>ユーザーのデータ</h2>
  <div v-for="user in users">
    <p>Name: {{ user.firstName + ' ' + user.lastName }}</p>
    <!-- <p>{{ fullName }}</p> -->
    <p v-if="user.isMember">メンバーです</p>
    <p v-else>メンバーではありません</p>
  </div>
</template>

<style>
.red {
  color: red;
}
</style>
