# vueex0203
```
<!DOCTYPE html>
<html lang="en">
 <head>
 </head>
 <body>
 <div>
<div id = "app" > </div>
</div>
<script src="https://unpkg.com/vue@next"></script>
   <script>

      const vm = Vue.createApp({
	  template: `<div>{{ greeting }} 好棒棒 ! </div>`,
	  data() {
		return {
			greeting : 'hello vue.js!'
			}
		}
	}).mount('#app');
   </script>   
 </body>    	
</html>



```
# 0201
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
<div id="app">
<p> 總金額共 {{subtotalComputed}} 元 </p>
<p> 總金額共 {{subtotalComputed}} 元 </p>
<p> 總金額共 {{subtotalComputed }} 元 </p>
<p> 總金額共 {{subtotalMethods() }} 元 </p>
<p> 總金額共 {{subtotalMethods() }} 元 </p>
<p> 總金額共 {{subtotalMethods() }} 元 </p>
</div>
	<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
	data () {
	return {
		message: 'Hello Vue!'
		}
	},
	computed: {
	subtotalComputed: function() {
		console.log('computed');
			return 100 * 100;
		}
	},
	methods: {
		subtotalMethods: function() {
			console.log('methods');
		return 100 * 100;
		}
	}
	}).mount('#app')
  </script>
 </body>    	
</html>




```

# 0204
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
	<div id="app">
	<p> 總金額共 {{ subtotalComputed()}} 元  </p>
	<p> 總金額共 {{ subtotalComputed() }} 元 </p>
	<p> 總金額共 {{ subtotalComputed() }} 元 </p>
	
	<p> 總金額共 {{ subtotalMethods() }} 元 </p>
	<p> 總金額共 {{ subtotalMethods() }} 元 </p>
	<p> 總金額共 {{ subtotalMethods() }} 元 </p>
	</div>
	<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
     data() {
		return {
			quantity : 100,
			price :100
		}
	  },
	  computed : {
		subtotalComputed : function () {
			console.log('computed');
			return this.quantity * this.price;
		}
	  },
	  methods : {
		subtotalMethods : function () {
			console.log('methods');
			return this.quantity * this.price;
		}
	  }
	}) .mount('#app');
  </script>
 </body>    	
</html>

```
# 0202
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
<div id="app">
	<p>1 日幣 = 0.278台幣 </p>
	<div>台幣 <input type="text" v-model="twd"></div>
	<div>日幣 <input type="text" v-model="jpy"></div>
</div>

	<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
    data() {
	  return {
		twd: 0.278,
	  }
	 },
	 computed:{
		jpy:{
			get(){
				return Number.parseFloat(Number(this.twd)/0.278).toFixed(3);
			},
			set(val){
				this.twd = Number.parseFloat(Number(val)*0.278).toFixed(3);
				}
			}
		}
	}).mount('#app')
  </script>
 </body>    	
</html>

```
# 0204美金
```
<!DOCTYPE html>
<html lang="en">
 <head>

 </head>
 <body>
<div id="app">
	<p>假設,1日幣 = 0.278 台幣 ,且 1 美金 = 28.540台幣 </p>
	<div>台幣 <input type="text" v-model="twd"></div>
	<div>日幣 <input type="text" v-model="jpy"></div>
	<div>美金 <input type="text" v-model="usd"></div>
</div>

	<script src="https://unpkg.com/vue@next"></script>
<script>
   const vm = Vue.createApp({
    data() {
	  return {
		twd: 1000,
	  }
	 },
	 computed:{
		jpy:{
			get(){
				return Number.parseFloat(Number(this.twd)/0.278).toFixed(3);
			},
			set(val){
				this.twd = Number.parseFloat(Number(val)*0.278).toFixed(3);
				}
			},
		usd:{
			get(){
				return Number.parseFloat(Number(this.twd)/28.540).toFixed(3);
			},
			set(val){
				this.twd = Number.parseFloat(Number(val)*28.540).toFixed(3);
				}
			}
		}
	}).mount('#app')
  </script>
 </body>    	
</html>
```
