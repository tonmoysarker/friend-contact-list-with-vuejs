<template>
    <li>
        <h2>
            {{ friend.name }}
            <span v-show="friend.isFavourite">(Favourite)</span>
        </h2>
        <button @click="toggleFavourite">Toggle Favourite</button>
        <button @click="toggleDetails">
            {{ detailsAreVisible ? "Hide" : "Show" }} Details
        </button>
        <ul v-if="detailsAreVisible">
            <li>
                <strong>Phone:</strong>
                {{ friend.phone }}
            </li>
            <li>
                <strong>Email:</strong>
                {{ friend.email }}
            </li>
        </ul>
    </li>
</template>

<script>
export default {
    props: {
        receivedFreind: {
            type: Object,
            required: true,
        },
        receivedFavourite: { type: Boolean, required: false, default: false },
    },
    emits: ["toggle-favourite"],
    data() {
        return {
            detailsAreVisible: false,
            friend: this.receivedFreind,
        };
    },
    methods: {
        toggleDetails() {
            this.detailsAreVisible = !this.detailsAreVisible;
        },
        toggleFavourite() {
            this.$emit("toggle-favourite", this.friend.id);
        },
    },
};
</script>
