<template>
    <div class="my-component">
        <div>{{ reverseMessage  }}</div>
        <div><button @click="changeText">Change text</button></div>
        <div><button @click="changeType">Change type</button></div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                message: {
                    text: this.sayHello(),
                    type: "greeting"
                }
            }
        },
        methods: {
            sayHello() {
                return 'this function return value'
            },
            changeText() {
                this.message.text = this.reverseMessage;
            },
            changeType() {
                this.message.type = 'this is new type'
            }
        },
        computed: {
            reverseMessage() {
                return this.message.text.split('').reverse().join('')
            },
            getText() {
                return this.message.text
            },
            getType() {
                return this.message.type
            }
        },
        watch: {
            message: {
                handler: function() {
                    console.log('message is changed')
                },
                deep: true
            },
            reverseMessage() {
                console.log('conputed is changed')
            },
            getText() {
                console.log('text is changed')
            },
            getType() {
                console.log('type is changed')
            }
        }
    }
</script>

<style lang="scss" scoped>
    .my-component {
        color: red;
    }
</style>