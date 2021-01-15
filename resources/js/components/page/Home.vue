<template>
    <div>
        <main>
            <div class="container">
                <article class="col-md-8 col-xs-12">
                    ・
                    ・
                    ・
                </article>
                <the-sidebar></the-sidebar>
            </div>
        </main>
    </div>
</template>

<script>
import TheSidebar from "../layout/TheSidebar";
import BarChart from "../module/BarChart";

export default {
    components: {
        TheSidebar,
        BarChart
    },
    data() {
        return {
            categories: [1],
            information: [],
            category: [],
        };
    },
    mounted() {
        this.$http.get("/api/category").then(response => {
            this.category = response.data;
        });
        this.$http.get("/api/information").then(response => {
            this.information = response.data;
        });
    },
    methods: {
        goQuiz() {
            this.$router.push("/quiz?categories=" + this.categories);
        }
    }
};
</script>
