<template>
    <div>
        <H1>{{ title }}</H1>
        <input :value="input_text_one" @input="$emit('test', $event.target.value)" />

        <input :value="value" @input="$emit('input',$event.target.value)" />

        <input :value="input_text_three" @input="$emit('update:input_text_three', $event.target.value)"/> 
        <div class="flex-con">
            <div @click="flexOne" class="flex-item">1</div>
            <div @click="flexTwo" class="flex-item">2</div>
            <div @click="flexThree" class="flex-item">3</div>
        </div>
        <input type="checkbox" @change="changeTickBox"/>


        <button @click="sendMessagToParent">Submit</button>
    </div>
</template>

<script>

export default {
    name:'childForm',
    props:{
        title: {
            type: String,
            default: '',
            required: true
        },
        input_text_one: {
            type: String
        },
        value: {
            type: String
        },
        input_text_three: {
            type: String
        }
    },
    data(){
        return {
            check: false
        }
    },
    methods: {
        sendMessagToParent: function(e){
            this.$emit('showAlert', e);
        },
        flexOne: function(){
            this.$emit('showFlex', "1");
        },
        flexTwo: function(){
            this.$emit('showFlex', "2");
        },
        flexThree: function(){
            this.$emit('showFlex', "3");
        },
        changeTickBox: function(){
            this.check = !this.check;
            this.$emit('CheckBoxMessageAlert', this.check);
        }
    },
}
</script>

<style scoped>

button {
    display: block;
}

.flex-con {
    display: flex;
}

.flex-item {
    width: 100px;
    height: 150px;
    border: 3px solid green;
    margin: 1em;
}
</style>