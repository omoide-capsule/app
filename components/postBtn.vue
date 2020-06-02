<template>
  <div class="post-button" @click="$emit('click')">保存</div>
</template>
<style>
.post-button {
  margin-top: 30px;
  background-color: #3b5f8a;
  color: #ffffff;
  width: 60%;
  border-radius: 30px;
  text-align: center;
  font-weight: bold;
  box-shadow: -2px 2px 2px 2px #eeeeee;
  transition: 1s;
  margin: 20px;
  line-height: 40px;
  font-size: 14pt;
  padding: 5px;
}

.post-button:hover {
  box-shadow: -3px 3px 3px 3px #eeeeee;
  background-color: #3b5f8aef;
}
</style>
