<template>
  <div class="messageboard-page">
    <aside class="messageboard__sidebar">
      <section class="sidebar__header">
        <h1>Chat</h1>
      </section>
      <section class="sidebar__cotent">
        <h2>Users</h2>
        <ul class="sidebar__userlist">
          <li v-for="user in users" class="siderbar__userlist-item">
            <div class="userlist__initials g__initials-rounded-circle"><span>{{ user.first_initial }}</span><span>{{
              user.second_initial }}</span></div>
            <p class="userlist__username">{{ user.username }}</p>
          </li>
        </ul>
      </section>
      <section class="sidebar__footer">
        <img src="../assets/img/Vector.svg" alt="">
        <router-link :to="{ name: 'home' }">Log out</router-link>
      </section>
    </aside>
    <section class="messageboard__mainfeed">
      <section class="mainfeed__header">
        <div class="mainfeed__header-currentuser">
          <div class="currentuser__initials g__initials-rounded-circle">PK</div>
          <h1 class="currentuser__name">Prodip Kumar</h1>
        </div>
        <div class="mainfeed__header-filters">
          <button class="filter-btn filter-btn--active">All</button>
          <button class="filter-btn">Today</button>
          <button class="filter-btn">Last 7 days</button>
        </div>
      </section>
      <section class="mainfeed__content">
        <!-- <div class="mainfeed__message-wrapper">
          <div class="mainfeed__currentusermessage">
            <p>Maybe tomorrow</p>
          </div>
          <p class="message-timestamp">11.30 PM</p>
        </div> -->

        <div v-for="message in messages" class="mainfeed__message-wrapper">
          <div class="currentusermessage__wrapper" v-if="message.username == 'Prodip Kumar'">
          <div class="mainfeed__currentusermessage">
            <p>{{ message.message_body }}</p>
          </div>
          <p class="message-timestamp">{{ message.time_stamp }}</p>
        </div>

        <div v-else>
          <div class="mainfeed__otherusermessage">
            <p>{{ message.message_body }}</p>
          </div>
            <p class="message-timestamp">{{ message.username }} - {{ message.time_stamp }}</p>
        </div>
      </div>
      </section>
      <section class="mainfeed__footer">
        <form class="message__input-form" @submit.prevent="post_message()">
        <input v-model="written_message" class="mainfeed__message-input" type="text" placeholder="Write a message">
        <button class="mainfeed__message-send"><img src="../assets/img/send.svg" alt=""></button>
      </form>
      </section>
    </section>
  </div>
</template>

<style lang="scss" src="../assets/css/views/MessageBoardView.scss"></style>

<script>

export default {
  data() {
    return {
      written_message: '',
      users: [
        {
          first_initial: 'P',
          second_initial: 'K',
          username: 'Prodip Kumar'
        },
        {
          first_initial: 'J',
          second_initial: 'N',
          username: 'Julkar Nayein'
        },
        {
          first_initial: 'S',
          second_initial: 'B',
          username: 'Sanaz Bahmani'
        }
      ],
      messages: [
        {
          username: 'Prodip Kumar',
          message_body: 'After we go back to SG ',
          time_stamp: '11.30 PM'
        },
        {
          username: 'Prodip Kumar',
          message_body: 'Maybe tomorrow',
          time_stamp: '11.30 PM'
        },
        {
          username: 'Aleck',
          message_body: 'Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem.',
          time_stamp: '11.00 PM'
        },
        {
          username: 'Benkaii',
          message_body: 'Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem.',
          time_stamp: '11.10 PM'
        },
        {
          username: 'JJ Jinggg',
          message_body: 'Ron, when you’ll book a plane ticket?',
          time_stamp: '09.40 PM'
        },
        {
          username: 'Jason Susanto',
          message_body: 'Hahaha, lol',
          time_stamp: '9.27 PM'
        }
      ]
    }
  },
  methods: {
    post_message() {
      let x = this.written_message
      this.messages.unshift({
          username: 'Prodip Kumar',
          message_body: x,
          time_stamp: '12.00 AM'
        })
    }
  }
}
</script>
