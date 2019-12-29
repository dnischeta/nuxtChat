<template>
  <div>
    <div v-if="name === 'admin'" class="message--system">
      <p class="message__text text-xs-center">{{ text }}</p>
      <hr />
    </div>
    <div v-else class="message__wrapper">
      <div class="message--default" :class="{ owner }">
        <small>
          <strong>{{ name }}</strong>
        </small>
        <p class="message__text">{{ text }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    name: String,
    text: String,
    owner: {
      type: Boolean,
      default: false
    }
  }
};
</script>

<style scoped>
.message--system {
  margin-bottom: 1rem;
}

.message--default {
  padding: 1rem;
  width: 60%;
  margin: 0 1rem;
  box-shadow: 0 1px 0 0 rgba(50, 50, 50, 0.3);
  border-radius: 4px;
  background-color: #1976d2;
  position: relative;
  margin-bottom: 1rem;
}

.message--default p {
  margin-bottom: 0;
}

.message--default.owner {
  background-color: #fff;
  color: #000;
  align-self: flex-end;
}

.message__text {
  margin-bottom: 1rem;
}

.message__wrapper {
  display: flex;
  flex-direction: column;
}
</style>