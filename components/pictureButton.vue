<template>
  <div class="picture-button">
    写真を追加
    <span style="line-height:30vh"
      ><v-icon color="#3b5f8a">mdi-camera</v-icon></span
    >
  </div>
</template>
<style>
.picture-button {
  color: #3b5f8a;

  border-radius: 10px;
  text-align: center;
  font-weight: bold;
  height: 30vh;
  box-shadow: -2px 2px 2px 2px #eeeeee;
  transition: 1s;
  margin-right: 20px;
  margin-left: 20px;
}

.picture-button:hover {
  box-shadow: -6px 6px 3px 3px #eeeeee;
}
</style>
