<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title">{{ itemTitle }}</h5>
            <p class="card-text">{{ content }}</p>
            <h3>{{ price }}</h3>
        </div>
    </div>
</template>

<script>
export default {
    props: { itemTitle: String, content: String, price: Number },

    mounted() {
        console.log("item", this.itemTitle);
    },
};
</script>
