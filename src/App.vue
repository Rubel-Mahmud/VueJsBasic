<template>
    <br>
    <div class="container">
        <button @click="componentToRender='compHome'" class="btn btn-primary">Home</button>
        <button @click="componentToRender='compAbout'" class="btn btn-primary">About</button>
        <button @click="componentToRender='compContact'" class="btn btn-primary">Contact</button>
        
        <keep-alive>
            <component :is="componentToRender"></component>
        </keep-alive>

    </div>
</template>


<script>
    import compHome from './Components/home_component'
    import compAbout from './Components/about_component'
    import compContact from './Components/contact_component'
    export default{
        data(){
            return {
                componentToRender : 'compHome'
            }
        },

        components : {
            'compHome' : compHome,
            'compAbout' : compAbout,
            'compContact' : compContact
        }
    }
</script>

<style></style>