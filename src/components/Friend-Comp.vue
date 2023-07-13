<template>
    <li>
        <div>
            <strong>Name: </strong> {{ name }}
        </div>
        <div>
            <strong>Phone: </strong> {{ phone }}
        </div>
        <div>
            <strong>Email: </strong> {{ email }}
        </div>
        <div>
            <strong>Is Favourite: </strong> {{ isFavourite ? "Yes" : "No" }}
        </div>
        <div>
            <button @click="toggleFavourite()">Toggle Favourite</button>
        </div>
    </li>
</template>

<script>
    export default {
        // props: ['name', 'phone', 'email', 'isFavourite'],
        props: {
            id: {
                type: String,
                required: true
            },
            name: {
                type: String,
                required: true
            },
            phone: {
                type: String,
                required: true
            },
            email: {
                type: String,
                required: true
            },
            isFavourite: {
                type: Boolean,
                required: false,
                default: false
            }
        },
        emits: {
            'on-favourite': function(id) {
                return !!id;
            }
        },
        data() {
            return {
            }
        },
        methods: {
            toggleFavourite () {
                this.$emit('on-favourite', this.id);
            }
        }
    }
</script>
