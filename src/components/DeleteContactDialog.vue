<template>
  <v-dialog v-model="dialog" persistent max-width="290">
    <v-card>
      <v-card-text>Delete this Contact?</v-card-text>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn flat @click.native="$emit('close')">Cancel</v-btn>
        <v-btn flat color="red" @click="remove">Yes, delete this.</v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>      
</template>
<script>
    export default {
      props: ['dialog', 'id'],
      methods: {
        async remove () {
          this.$emit('close')
          this.$router.replace('/')
          await this.$store.dispatch('deletePerson', this.id)
          this.$store.dispatch('addToast', {text: 'Successfully deleted contact.', color: 'success'})
        }
      }
    }
</script>