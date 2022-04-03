<template>
  <div class="profile" >
    <img class="profile__avatar" :src="avatar" alt="avatar">
    <div class="profile__info">
      <p class="profile__name">{{name}}</p>
      <p class="profile__item profile__age">{{age}}</p>
      <p class="profile__item profile__work">{{employment}}</p>
    </div>
  </div>
</template>
<script>
export default {
  props: [
    "name", "age", "employment", "avatar"
  ]
}
</script>
<style scoped>
.profile {
  display: flex;
  border-bottom: 1px solid #c2c2c2;
  padding-bottom: 10px;
}
.profile__avatar {
  width: 100px;
  height: 100px;
  border-radius: 20%;
  margin: 20px 0 0 20px;
}
.profile__info {
  margin: 20px 0 0 20px;
  font-size: 22px;
  min-width: 200px;
}
.profile__item {
  margin-top: 10px;
}
.profile__work {
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
}
.profile__name::before {
  content: 'Имя:';
  margin-right: 10px;
}
.profile__age::before {
  content: 'Возраст:';
  margin-right: 10px;
}
.profile__work::before {
  content: 'Место работы:';
  margin-right: 10px;
}
@media screen and (max-width: 650px) {
  .profile__info {
    font-size: 14px;
    margin-left: 10px;
  }
  .profile__avatar {
    width: 40px;
    height: 40px;
    margin: 30px 0 0 10px;
  }
}

</style>