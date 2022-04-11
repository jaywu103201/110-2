
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
# 0404
```
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Hello Vue</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.min.css">
  <style>
   #app {
    display: block;
    overflow: hidden;
    width: 100%;
   }
   h4 {
    margin: 1rem 0;
    font-size: 1rem;
   }

  .modal-mask {
    position: absolute;
    z-index: 10;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: table;
    background-color: rgba(0, 0, 0, .5);
    transition: opacity .3s ease;
  }

  .modal-container {
    cursor: pointer;
    display: table-cell;
    vertical-align: middle;
  }

  .modal-body {
    cursor: auto;
    display: block;
    width: 50%;
    margin: 0 auto;
    padding: 2rem;
    background-color: #fff;
  }
  </style>
</head>

<body>
<div id="app">
<h4> togglemModal with .self</h4>

<div class="modal-mask" :style="modalStyle">
	<div class="modal-container" @click.self="togglemModal">
		<div class="modal-body">Hello!</div>
	</div>
</div>
	<button @click="isShow=true">Click Me</button>
</div>
<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
    data:()=> {
	  return {
		isShow: false
	   }
	 },
	 computed: {
		modalStyle() {
			return{
			'display':this.isShow ?'':'none'
			};
		  }
		},
	methods:{
		togglemModal(){
			this.isShow=!this,isShow;
		}
	  }
	}).mount('#app');
  </script>
</body>

</html>
```
# 0405
```
<div id="app">
	<p>Count: {{ count }}</p>
	<button @click.once="plus">Plus once</button>
</div>
<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
    data:()=> {
	  return {
		count:0
	   }
	 },
	methods:{
		plus: function(){
			this.count++;
		}
	  }
	}).mount('#app');
  </script>
 </body>    	
</html>
```
# 0406
```
<div id="app">
 <p>你按下的按鍵是: {{ pressKey }}</p>
 <input type="text" @keyup="press">
</div>
<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
    data:()=> {
	  return {
		pressKey:''
	   }
	 },
	methods:{
		press(event){
		this.pressKey=event.key;
		
		window.setTimeout(()=>{
			event.target.value='';
		},300)
	  }
	 }
	}).mount('#app');
  </script>
 </body>    	
</html>
```
# 0407
```
<div id="app">
<div class="messages">
	<div v-for="m in messages">{{m}}</div>
</div>
<input type="text"
	placeholder="please keyin any chars then type enter"
	v-model.trim="msg"
	@keydown.enter="addToMessages">
</div>

<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
    data() {
	  return {
		msg:'',
		messages:[]
	   }
	 },
	methods:{
	addToMessages(){
	this.messages.push(this.msg);
	this.msg='';
		}
	  }
	}).mount('#app');
  </script>
 </body>    	
</html>
```
