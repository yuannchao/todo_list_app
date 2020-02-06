<template>
    <div class="header">
        <div class="header__progressbar" role="progressbar" aria-valuenow="60" aria-valuemin="0" aria-valuemax="100"
            :style="{width: (todoCount / maxTodos) * 100 + '%'}">
            {{ todoCount }} / {{ maxTodos}}
        </div>
        <div class="header__display">
            <h2 class="header__display--time"> {{ time }} </h2>
            <h3 class="header__display--title">what's your daily focus ?</h3>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['todoCount', 'maxTodos'],
        data() {
            return {
                time: ''
            }
        },
        methods: {
            displayTime() {
                var now, hour, minute;
                now = new Date();

                hour = now.getHours();
                minute = now.getMinutes();
                if (minute <=9){
                    minute = "0" + minute
                }
                this.time = `${hour}:${minute}`;
            },
        },
        created() { 
            setInterval(this.displayTime , 1000)
        }
    }
</script>

<style>

</style>