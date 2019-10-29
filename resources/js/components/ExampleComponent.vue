<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Example Component</div>

                    <div class="card-body" @click="bodyClicked($event)">
                        {{ users.name }}
                        <ul @click.stop="ulClicked($event)">

                            <li>HAHAHA</li>
                            <!-- <li v-for="user in users" v-bind:key="user.id">{{user.name}}</li> -->
                        </ul>

                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="style" scoped>

</style>

<script>

    export default {
        props: ['prenom'],
        data: function(){
            return {
                users: '',
                name:  "",
                id: 19
            }
        },

        
        methods: {
            bodyClicked(event){
                alert('BODY CLICKED')
                console.log(event);
            },
            ulClicked(event){
                alert('UL CLICKED');
            }
        },
        mounted() {
            // alert(this.prenom)
            axios.get('users/' + this.id)
                .then(data => {
                    this.users = data.data
                })
        }
    }
</script>
