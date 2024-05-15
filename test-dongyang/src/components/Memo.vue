<template>
    <div class="todo">
        <h3>메모장</h3>
        <textarea class="memo"></textarea>
    </div>
</template>

<script>
export default {
  name: 'MemoItem'
}
</script>

<style>
 .memo {
    width: 300px;
    height: 310px;
    resize: none;
    border-radius: 10px;
    border: 1px solid #cccccc00;
    font-size: 20px;
    box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.3);
 }
</style>
