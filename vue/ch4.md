
# 0401
```
<!DOCTYPE html>
<html lang="en">
<head>
</head>
 <body>
<div id="app">

<p>Count :{{count}}</p>
<button v-on:click="count++">Plus</button>

<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
    data() {
	  return {
		count :0
	   }
	 }
	}).mount('#app')
  </script>
 </body>    	
</html>
```
# 0403
```
<!DOCTYPE html>
<html lang="en">
<head>
</head>
<body>
<div id="app">
<p><input v-model.number="amount"></p>
<p>Count : {{count}}</p>
<button v-on:click="plus(amount,$event)">Plus</button>
</div>
<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
    data() {
	  return {
		amount:0,
		count :0
	   }
	 },
	methods:{
	plus(amount,event){
	//"BUTTON"
		console.log(event.target.tagName);
		this.count +=amount;
		}
		}
	}).mount('#app');
  </script>
 </body>    	
</html>
```

