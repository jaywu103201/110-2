# 0301
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
<div id="app">
	<p v-bind:id="customId"> show time</p>

</div>

	<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
    data() {
	  return {
		customId :'item_id-1'
	  }
	 }
	}).mount('#app')
  </script>
 </body>    	
</html>
```

# 0301a
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
<div id="app">
<button v-bind:disabled="isBtnDisabled">click me!</button>
	
</div>

	<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
    data() {
	  return {
		isBtnDisabled:false
	  }
	 },
	}).mount('#app')
  </script>
 </body>    	
</html>
```
# 0302
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
<div id="app">
<input v-model="message" placeholder = "edit me">
<p>Message is: {{message}}</p>
	
</div>

	<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
    data() {
	  return {
		message: 'hi,ksu!'
	  }
	 },
	}).mount('#app')
  </script>
 </body>    	
</html>
```
# 0303
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
<div id="app">
<p><span style="color:green;font-weight:bold">the message is:</span>{{message}}</p>

<textarea v-model="message" placeholder="blank..."></textarea>
</div>

	<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
    data() {
	  return {
		message: 'hi,ksu!'
	  }
	 }
	}).mount('#app')
  </script>
 </body>    	
</html>
```
# 0304
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
<div id="app">
<p>
<input type="radio" id="one" value="1" v-model="picked">
<label for="one">one</label>
</p>
<p>
<input type="radio" id="two" value="2" v-model="picked">
<label for="one">two</label>
</p>
<span style="color:green;font-weight:bold">
	the picked radio button is {{picked}}</span>
</div>

	<script src="http://unpkg.com/vue@next"></script>

<script>
	const vm = Vue.createApp({
		data()	{
			return	{
				picked : 2
			}
		}
	}).mount('#app');
</script>
</body>    	
</html>
```
# 0305
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
<div id="app">
<p>
<input type="checkbox" id="jack" value="jack" v-model="checkedNames">
<label for= jack">jack</label>
</p>
<p>
<input type="checkbox" id="john" value="john" v-model="checkedNames">
<label for="john">john</label>
</p>
<p>
<input type="checkbox" id="mike" value="mike" v-model="checkedNames">
<label for="mike">mike</label>
</p>
<p>
<input type="checkbox" id="mary" value="mary" v-model="checkedNames">
<label for="mary">mary</label>
</p>
<br>
<p>checked Namms : {{checkedNames}} </p>
</div>

	<script src="http://unpkg.com/vue@next"></script>

<script>
	const vm = Vue.createApp({
		data()	{
			return	{
				checkedNames:[]
			}
		}
	}).mount('#app');
</script>
</body>    	
</html>
```
# 0306
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
<div id="app">
<input type="checkbox" id="checkbox" v-model="isChecked">
<label for = "checkbox">status : {{isChecked}}</label>
</div>

	<script src="http://unpkg.com/vue@next"></script>

<script>
	const vm = Vue.createApp({
		data()	{
			return	{
				isChecked:false
			}
		}
	}).mount('#app');
</script>
</body>    	
</html>
```
# 0307
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
<div id="app">
<select v-model="selected">
<option disabled value="">please choose</option>
<option>taipei</option>
<option>tainan</option>
<option>kaohshing</option>
</select>

<p> the selected items : {{selected || 'no option'}}</p>
</div>

	<script src="http://unpkg.com/vue@next"></script>

<script>
	const vm = Vue.createApp({
		data()	{
			return	{
				selected: ''
			}
		}
	}).mount('#app');
</script>
</body>    	
</html>
```
# 0308
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
<div id="app">
<input v-model.lazy="message" placeholder="edit me">
<p>message with ".lazy" : {{message}}</p>
<hr>

<p>
v=model with .number:
<input v-model.number="num1">+
<input v-model.number="num2">= {{sum}}
</p>
<hr>
<input v-model.trim="message2" placeholder="edit me">
<p>message with ".trim" is:{{message2}}</p>
</div>

	<script src="http://unpkg.com/vue@next"></script>

<script>
	const vm = Vue.createApp({
		data()	{
			return	{
				message: 'hi',
				message2: '  hi  ',
				num1:0,
				num2:0,
			}
		},
		computed:{
		sum() {
			return this.num1 + this.num2;
			}
		}
	}).mount('#app');
</script>
</body>    	
</html>
```
# 0309vtext
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
<div id="app">
<div v-text="text"></div>
</div>

	<script src="http://unpkg.com/vue@next"></script>

<script>
	const vm = Vue.createApp({
		data()	{
			return	{
				text: '<h1>hello</h1>'
			}
		},
	}).mount('#app');
</script>
</body>    	
</html>
```
# 0309vhtml
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
<div id="app">
<div v-text="text"></div>
</div>

	<script src="http://unpkg.com/vue@next"></script>

<script>
	const vm = Vue.createApp({
		data()	{
			return	{
				text: '<h1>hello</h1>'
			}
		},
	}).mount('#app');
</script>
</body>    	
</html>
```
```
v-text 會輸出 '' 中所有字元包括 <h1></h1>
v-html 等於使用html語法,會把 <h1></h1> 變成字體大小
```
# 0309
```
<!DOCTYPE html>
<html lang="en">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Hello Vue</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.min.css">
  <style>
    body {
      padding: 1rem;
    }

    #app>div {
      margin: 1rem 0;
    }

    input {
      width: 300px;
      padding: 3px;
    }

    .text,
    .html {
      border: 1px solid #aaa;
      padding: 10px 5px;
    }
  </style>
 </head>
 <body>
<div id="app">
	Edit:<input type="text" v-model="rawContent">
	
	<div>
		v-text:
		<div class="text" v-text="rawContent"></div>
	</div>
	
	<div>
		v-html:
		<div class="html" v-html="rawContent"></div>
	</div>
	
	<div>
		v-text with "v-once":
		<div class="html" v-text="rawContent"></div>
	</div>
</div>

	<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
    data() {
	  return {
		rawContent:'<h1>Hi KSU!</h1>'
	  }
	 }
	}).mount('#app');
  </script>
 </body>    	
</html>
```
# 0310
```
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Hello Vue</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.min.css">
  <style>
    body {
      padding: 1rem;
    }

    p {
      margin: 1rem 0;
    }

    input {
      width: 300px;
      padding: 3px;
    }

    .error {
      color: red;
      border: solid 1px red;
    }
  </style>
</head>

<body>

	<div id="app">
		<input type="text" v-model.trim="message" placeholder="請勿超過十個字" :style="msgStyle">
	</div>

<script src="https://unpkg.com/vue@next"></script>
	<script>
		const vm = Vue.createApp({
			data () {
				return{
					message:''
				}
			},
			computed:{
				isVaild: function(){
					return this.message.length <= 10;
				},
				msgStyle: function() {
					return {
						'border':this.isVaild ?'':'red solid 1px',
						'color':this.isVaild ?'':'red'
					};
				}
			}
		}).mount('#app');
	</script>
 </body>    
</html>

```
