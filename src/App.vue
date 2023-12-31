<template>
    <section class="container mt-5">
        <header class="bg-primary text-white p-3 rounded mb-3">
            <h1>My Friends</h1>
        </header>

        <!-- Using Bootstrap's row and columns for layout -->
        <div class="row">
            <!-- Contact Form Column -->
            <div class="col-md-6 mb-3">
                <contact-form @add-friend="addFriend"></contact-form>
            </div>

            <!-- Friends List Column with Scroll -->
            <div class="col-md-6">
                <ul
                    v-auto-animate
                    class="list-group overflow-auto"
                    style="max-height: 400px"
                >
                    <friend-contact
                        v-for="friend in friends"
                        :key="friend.id"
                        :receivedFreind="friend"
                        @toggle-favourite="toggleFavourite"
                        class="list-group-item"
                    ></friend-contact>
                </ul>
            </div>
        </div>
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
    methods: {
        toggleFavourite(friendId) {
            const targetFriend = this.friends.find(
                (friend) => friend.id === friendId
            );
            targetFriend.isFavourite = !targetFriend.isFavourite;
        },
        addFriend(friend) {
            this.friends.push(friend);
        },
    },
};
</script>

<!-- No need for custom styles, as Bootstrap will handle it -->
