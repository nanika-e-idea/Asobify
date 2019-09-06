<template>
    <div class="task">
    <div class="description">
      <template v-if="!this.isEdit">
        <div v-on:click="startEdit">
        <h3>TaskName...</h3>
        <p>After second lines...</p>
        </div>
      </template>
      <template v-if="this.isEdit">  
          <textarea>### TaskName...
After second lines...
          </textarea>
      </template>
    </div>
    
    <div class="schedule">
      <div class="startDate">
        <div class="view">YYYY/MM/DD</div>
        <div class="edit hidden"></div>
      </div>
      <span>-</span>
      <div class="endDate">
        <div class="view">YYYY/MM/DD</div>
        <div class="edit hidden"></div>
      </div>
    </div>
    <div class="status">
        <div class="wiew"></div>
        <div class="edit"></div>
    </div>
    <div class="performer"></div>
    <div class="note">
      <textarea>note,note,note,note,note,note</textarea>
    </div>
        <template v-if="this.isEdit">
          <v-btn @click="endEdit">Save</v-btn>
          <v-btn @click="endEdit">Cancel</v-btn>
      </template>
  </div>
</template>

<script>
export default {
    data(){
    return {
      isEdit: false,
    }
  },
  methods: {
    startEdit: function() {
      this.isEdit = true;
    },
    endEdit: function() {
      this.isEdit = false;
    },
  },
}
</script>

<style lang="scss" scoped>
@import '~/assets/scss/base.scss';

</style>