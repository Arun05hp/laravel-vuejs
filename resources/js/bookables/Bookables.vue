<template>
    <div>
        Rows is {{ rows }}
        <div v-if="loading">Data is Loading</div>
        <div v-else>
            <div class="row" v-for="row in rows" :key="'row' + row">
                <div
                    class="col mb-4"
                    v-for="(bookable, columns) in bookablesInRow(row)"
                    :key="'row' + 'row' + columns"
                >
                    <BookableListItem
                        :item-title="bookable.title"
                        :content="bookable.content"
                        :price="bookable.price"
                    ></BookableListItem>
                </div>

                <div
                    class="col"
                    v-for="(p, columns) in placeholderInRow(row)"
                    :key="'prow' + 'prow' + columns"
                ></div>
            </div>
        </div>
    </div>
</template>

<script>
import BookableListItem from "./BookableListItem";
export default {
    components: {
        BookableListItem,
    },
    data() {
        return {
            bookables: null,
            loading: false,
            columns: 3,
        };
    },
    // beforeCreate() {
    //     console.log("breforeCreate");
    // },\\
    computed: {
        rows() {
            return this.bookables
                ? Math.ceil(this.bookables.length / this.columns)
                : 0;
        },
    },

    methods: {
        bookablesInRow(row) {
            return this.bookables.slice(
                (row - 1) * this.columns,
                row * this.columns
            );
        },
        placeholderInRow(row) {
            return this.columns - this.bookablesInRow(row).length;
        },
    },
    created() {
        this.loading = true;
        console.log("created");

        setTimeout(() => {
            this.bookables = [
                {
                    title: "Book 1 ",
                    content: "Book 1 description",
                    price: 1000,
                },
                { title: "Book 2", content: "Book 2 description", price: 1500 },
                {
                    title: "Book 1 ",
                    content: "Book 1 description",
                    price: 1000,
                },
                { title: "Book 2", content: "Book 2 description", price: 1500 },
                {
                    title: "Book 1 ",
                    content: "Book 1 description",
                    price: 1000,
                },
                { title: "Book 2", content: "Book 2 description", price: 1500 },
                {
                    title: "Book 1 ",
                    content: "Book 1 description",
                    price: 1000,
                },
                { title: "Book 2", content: "Book 2 description", price: 1500 },
            ];
            this.loading = false;
        }, 5000);

        // setTimeout(() => {
        //     this.bookable1.title = "Math Book";
        // }, 8000);

        // setTimeout(() => {
        //     this.bookable3.title = "Test Book";
        // }, 12000);
    },
    // beforeMount() {
    //     console.log("beforeMount");
    // },
    // mounted() {
    //     console.log("mounted");
    // },
    // beforeDestroy() {
    //     console.log("beforeDes");
    // },
    // destroyed() {
    //     console.log("destroyed");
    // },
};
</script>
