<template>    
        <tr>
            <td>{{ name }}</td>
            <td>{{ value }}</td>
        </tr>
</template>

<script>
    export default {
        props: ['name', 'value']        
    }
</script>

