<template>
  <div id="app">
    
    <child-form
    :title="title_parent"

    :input_text_one="text" @test="text = $event" 
    
    v-model="text_two"
    :input_text_three.sync="text_three"    
    @showFlex="boxAlertMessage($event)"
    @CheckBoxMessageAlert="cbAlert($event)" 
    @showAlert="inputAlertMessage($event)"/>
    <p>Input Text One:{{ text }}</p>
    <p>Input Text Two:{{ text_two }}</p>
    <p>Input Text Three:{{ text_three }}</p>
  </div>

  <!-- :value="text_two" @input="text_two = $event" -->
</template>

<script>
import ChildForm from './components/ChildFrom.vue'

export default {
  name: 'App',
  components: {
    ChildForm
  },
  data() {
    return {
      title_parent: 'Emit Exercise',
      text: '',
      text_two: '',
      text_three: ''
    }
  },
  methods: {
      inputAlertMessage: function(a){
        
        alert(a);
      },
      boxAlertMessage: function(boxNumber){
      alert("Box number " + boxNumber);
    },
    cbAlert: function(cbState){
      alert(cbState);
    }
  } 
}
</script>

<style>
</style>
