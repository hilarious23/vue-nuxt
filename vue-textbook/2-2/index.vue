<template>
    <script src="https://unpkg.com/vue@2.5.17"></script>
    <div id="app">
        <p>
            {{ message }}
        </p>
    </div>
</template>

<script>
    // ロードされ、Vueがグローバル変数として定義されているか確認
    console.assert(typeof Vue !== 'undefined');
      new Vue({
  	el:'#app',
    data: {
    	message: 'konichiwa'
    }
  });
</script>