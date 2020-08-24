<template>
    <div class="wrapper">
        <div class="title">
            LOGIN
        </div>
        <div class="rotate-in-ver">
            <img src="./logo.png" alt="">
        </div>
        <div class="login-input">
            <div>
                <label>
                    <input placeholder="ID"   class="blink-2"/>
                </label>
            </div>
            <div>
                <label >
                    <input placeholder="PASSWORD"   class="blink-2"/>
                </label>
            </div>
        </div>
        <div class="Sign">
            <div>
                <button class="jello-horizontal" type="button" >LOG IN</button>
            </div>
            <div>
                <router-link to="/signUp" tag="button" class="jello-horizontal">SIGN UP</router-link>
            </div>
        </div>
    </div>

</template>
<script>
    export default {
        name: "LoginComponent"
    }
</script>

<style lang="scss" scoped>
    @import './LoginComponent.scss';
</style>
