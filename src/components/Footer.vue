<script>

    export default{
        data(){
            return{
                date:new Date().getDate() + ' ' + new Date().toLocaleString('default', { month: 'long' }) + ' ' + new Date().getFullYear()}
        }
    }

</script>
<template>
    <footer class="footer sm:footer-horizontal footer-center bg-base-300 text-base-content p-4">
        <aside>
            <p>Copyright © {{ date }} - All right reserved by Omar Muhammad </p>
        </aside>
    </footer>
</template>