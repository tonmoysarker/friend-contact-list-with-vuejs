<template>
    <section class="container mt-5">
        <header class="bg-primary text-white p-3 rounded">
            <h1>My Friends</h1>
        </header>
        <contact-form @add-friend="addFriend"></contact-form>
        <ul class="list-group mt-3">
            <friend-contact
                v-for="friend in friends"
                :key="friend.id"
                :receivedFreind="friend"
                @toggle-favourite="toggleFavourite"
                class="list-group-item"
            ></friend-contact>
        </ul>
    </section>
</template>

<script>
export default {
    data() {
        return {
            friends: [
                {
                    id: "manuel",
                    name: "Manuel Lorenz",
                    phone: "0123 45678 90",
                    email: "manuel@localhost.com",
                    isFavourite: true,
                },
                {
                    id: "julie",
                    name: "Julie Jones",
                    phone: "0987 654421 21",
                    email: "julie@localhost.com",
                    isFavourite: false,
                },
            ],
        };
    },
    methods: {},
};
</script>

<!-- No need for custom styles, as Bootstrap will handle it -->
