<template>
    <form @submit.prevent="onSubmit">
        <div>
            <strong>Name: </strong> <input type="text" v-model="enteredName" required />
        </div>
        <div>
            <strong>Phone: </strong> <input type="text" v-model="enteredPhone" required />
        </div>
        <div>
            <strong>Email: </strong> <input type="email" v-model="enteredEmail" required />
        </div>
        <div>
            <button type="submit">Add Friend</button>
        </div>
    </form>
</template>

<script>
export default {
    emits: ['add-friend'],
    data () {
        return {
            enteredName: '',
            enteredPhone: '',
            enteredEmail: '',
        }
    },
    methods: {
        onSubmit() {
            this.$emit('add-friend', {
                name: this.enteredName,
                phone: this.enteredPhone,
                email: this.enteredEmail
            });
        }
    }
}
</script>