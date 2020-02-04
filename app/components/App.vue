<template>
    <Page class="page">
        <ActionBar class="action-bar" title="Product"></ActionBar>
        <GridLayout>
            <ListView for="p in product" class="list-group">
                <v-template>
                    <StackLayout class="list-group-item">
                        <Label :text="p.title" />
                    </StackLayout>
                </v-template>
            </ListView>
        </GridLayout>
    </Page>
</template>

<script>
    import * as http from "http";
    export default {
        data() {
            return {
                product: []
            };
        },
        mounted() { 
          http.getJSON("https://localhost:3000/products").then(result => {
            this.product = result.results;
            }, error => {
              console.log(error);
            });
        }
    };
</script>

<style scoped></style>
