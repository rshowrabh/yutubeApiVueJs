<template>
    <input type="text" @input='onInput'>
</template>

<script>
export default {
    name: 'searchBar',
   
    methods: {
        onInput: function(e){
            this.$emit('termChange', e.target.value)
        }
    }
}
</script>