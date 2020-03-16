<!-- HTML Tag -->
<template>
    <div>
        <span>
            <button>{{ message }}</button>
        </span>
    </div>
</template>

<!-- Javascript -->
<script>
export default{
    data: {
        message: "click this button"
    }
}
</script>

<!-- CSS Style -->
<style>
    span {
        font-size: 1.2em;
    }
</style>