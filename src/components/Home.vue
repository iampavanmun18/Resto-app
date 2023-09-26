<template>
    <h1>Hello User Welcome On Home Page</h1>
</template>

<script>
export default {
    name: 'Home',
    Mounted()
{
    let user= localStorage.getItem('user-info');

    if(user)
    {
        this.$router.push({name:'SignUp'});
    }
}
}
</script>
