# 0601
```
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Hello Vue</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.min.css">
</head>

<body>

  <div id="app">
	<p>Please open up u re browser tool to see...</p>
  </div>
 
  
  <script src="https://unpkg.com/vue@next"></script>
  <script>
    const vm = Vue.createApp({
		data(){
			return {
				msg: 'hello vue.js!'
			}
		},
		created(){
		conslole.log('created');
		},
		mounted(){
		consloe.log('mounted');
		},
		unmounted(){
		consloe.log('ummounted');
		},
	}).mount('#app');
  </script>

</body>

</html>
```
