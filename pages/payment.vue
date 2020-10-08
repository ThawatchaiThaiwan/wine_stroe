<template>
  <form>
    <v-text-field
      v-model="name"
      :error-messages="nameErrors"
      :counter="10"
      label="Name"
      required
      @input="$v.name.$touch()"
      @blur="$v.name.$touch()"
    ></v-text-field>
    <v-text-field
      v-model="email"
      :error-messages="emailErrors"
      label="E-mail"
      required
      @input="$v.email.$touch()"
      @blur="$v.email.$touch()"
    ></v-text-field>
    <v-text-field
      v-model="address"
      :error-address="addressErrors"
      label="Address"
      required
      @input="$v.address.$touch()"
      @blur="$v.address.$touch()"
    ></v-text-field>
    <v-text-field
      v-model="city"
      :error-city="cityErrors"
      label="city"
      required
      @input="$v.city.$touch()"
      @blur="$v.city.$touch()"
    ></v-text-field>
    <v-container>
      <v-overflow-btn
        class="my-2"
        :items="items"
        label="ธนาคาร"
        dense
      ></v-overflow-btn>
    </v-container>
    <v-file-input
      v-model="files"
      color="deep-purple accent-4"
      counter
      label="Slip"
      multiple
      placeholder="Select your files"
      prepend-icon="mdi-paperclip"
      outlined
      :show-size="1000"
    >
      <template v-slot:selection="{ index, text }">
        <v-chip v-if="index < 2" color="deep-purple accent-4" dark label small>
          {{ text }}
        </v-chip>
        <span
          v-else-if="index === 2"
          class="overline grey--text text--darken-3 mx-2"
        >
          +{{ files.length - 2 }} File(s)
        </span>
      </template>
    </v-file-input>
    <v-checkbox
      v-model="checkbox"
      :error-messages="checkboxErrors"
      label="Do you agree?"
      required
      @change="$v.checkbox.$touch()"
      @blur="$v.checkbox.$touch()"
    ></v-checkbox>
    <v-btn class="mr-4" @click="submit"> submit </v-btn>
    <v-btn @click="clear"> clear </v-btn>
  </form>
</template>
<script>
export default {
  data: () => ({
    items: [
      'ธนาคารไทยพาณิชย์',
      'ธนาคารกสิกร',
      'ธนาคารกรุงไทย',
      'ธนาคารออมสิน',
      'ธนาคารกรุงศรี',
    ],
  }),
}
</script>
