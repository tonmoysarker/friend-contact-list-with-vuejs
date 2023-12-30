<template>
    <form @submit.prevent="handleSubmit" class="mt-4">
        <div class="mb-3">
            <label for="name-input" class="form-label">Name:</label>
            <input
                type="text"
                class="form-control"
                id="name-input"
                name="name-input"
                v-model.trim.lazy="friend.name"
                placeholder="Enter name"
                required
            />
        </div>

        <div class="mb-3">
            <label for="phone-input" class="form-label">Phone:</label>
            <input
                type="text"
                class="form-control"
                id="phone-input"
                name="phone-input"
                v-model.trim.lazy="friend.phone"
                placeholder="Enter phone number"
                required
            />
        </div>

        <div class="mb-3">
            <label for="email-input" class="form-label">Email:</label>
            <input
                type="email"
                class="form-control"
                id="email-input"
                name="email-input"
                v-model.trim.lazy="friend.email"
                placeholder="Enter email"
                required
            />
        </div>

        <div class="mb-3 form-check">
            <input
                type="checkbox"
                class="form-check-input"
                id="fav-input"
                name="fav-input"
                v-model="friend.isFavourite"
            />
            <label class="form-check-label" for="fav-input"
                >Add to favourites?</label
            >
        </div>

        <button type="submit" class="btn btn-primary">Add Friend</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            friend: {
                name: "",
                phone: "",
                email: "",
                isFavourite: false,
            },
        };
    },

    methods: {
        handleSubmit() {
            this.$emit("add-friend", {
                id: this.friend.name.split(" ")[0],
                ...this.friend,
            });
            this.resetInput();
        },
        resetInput() {
            this.friend.name = "";
            this.friend.phone = "";
            this.friend.email = "";
            this.friend.isFavourite = false;
        },
    },
};
</script>

<style scoped>
form {
    padding: 0 10rem;
}
</style>
