<template>
    <li class="list-group-item border-top-0">
        <div class="d-flex justify-content-between align-items-center">
            <h2 class="mb-0">
                {{ friend.name }}
                <span
                    v-if="friend.isFavourite"
                    class="badge bg-warning text-dark ms-2"
                    style="font-size: 0.8em"
                >
                    Fav
                </span>
            </h2>

            <div>
                <button @click="toggleFavourite" class="btn btn-secondary me-2">
                    Toggle Favourite
                </button>
                <button @click="toggleDetails" class="btn btn-primary">
                    {{ detailsAreVisible ? "Hide" : "Show" }} Details
                </button>
                <!-- TODO: need to create delete button and handle functionality -->
            </div>
        </div>

        <ul v-if="detailsAreVisible" class="list-group mt-3">
            <li class="list-group-item">
                <strong>Phone:</strong> {{ friend.phone }}
            </li>
            <li class="list-group-item">
                <strong>Email:</strong> {{ friend.email }}
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
