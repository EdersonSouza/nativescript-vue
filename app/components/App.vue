<template>
    <Page class="page">
        <ActionBar class="action-bar" title="Product"></ActionBar>
        <GridLayout>
            <ListView for="p in products" class="list-group">
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
    import axios from "axios";
    export default {
        data() {
            return {
               
                products:new Object()
            };
        },
        created() { 
            axios({ method: "GET", "url": "http://192.168.1.3:3000/products" }).then(result => {
                 this.products = result.data;
            }, error => {
                console.error(error);
            });
          
        }
    };
</script>

<style scoped></style>
