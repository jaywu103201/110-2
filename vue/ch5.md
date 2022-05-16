# 0501
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
      padding: 1rem;
    }

    a {
      color: #3eaf7c;
      text-decoration: none;
    }

    .pagination {
      display: block;
      overflow: hidden;
      margin: 0 auto;
    }

    .page-item {
      cursor: pointer;
      font-size: 1rem;
      list-style: none;
      display: block;
      width: 40px;
      height: 30px;
      line-height: 30px;
      text-align: center;
      border: 1px solid #c4ead9;
      color: #3eaf7c;
      float: left;
      margin: 0;
      margin-right: -1px;
    }

    .page-item:hover {
      background-color: #eee;
    }
  </style>
</head>

<body>

  <div id="app">
	<ul class="pagination">
	<li class="page-item" @click.prevent><a class="page-link" href>&lt;</a></li>
	<li class="page-item" v-for="page in 10"@click.prevent>
		<a class="page-link" href>{{page}}</a>
	</li>
	<li class="page-item" @click.prevent><a class="page-link" href>&gt;</a></li>
	</ul>
  </div>
	</div>
  <script src="https://unpkg.com/vue@next"></script>

  <script>
    const vm = Vue.createApp({}).mount('#app');
  </script>

</body>

</html>
```
# 0501a
# herf 
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
      padding: 1rem;
    }

    a {
      color: #3eaf7c;
      text-decoration: none;
    }

    .pagination {
      display: block;
      overflow: hidden;
      margin: 0 auto;
    }

    .page-item {
      cursor: pointer;
      font-size: 1rem;
      list-style: none;
      display: block;
      width: 40px;
      height: 30px;
      line-height: 30px;
      text-align: center;
      border: 1px solid #c4ead9;
      color: #3eaf7c;
      float: left;
      margin: 0;
      margin-right: -1px;
    }

    .page-item:hover {
      background-color: #eee;
    }
  </style>
</head>

<body>

  <div id="app">
	<ul class="pagination">
	<li class="page-item" ><a class="page-link" href>&lt;</a></li>
	<li class="page-item" v-for="(page,key) in arr">
		<a v-bind:href="page"> {{key}} </a>
	</li>
	<li class="page-item">
		<li class="page-item" href>&gt;</a>
		</li>
	</ul>
  </div>
  
  <script src="https://unpkg.com/vue@next"></script>

  <script>
    const vm = Vue.createApp({
		data(){
			return {
			arr:{
				1:'https://elearning2.ksu.edu.tw/learn/index.php',
				2:'https://elearning2.ksu.edu.tw/learn/index.php',
				3:'https://elearning2.ksu.edu.tw/learn/index.php',
				4:'https://elearning2.ksu.edu.tw/learn/index.php'
			}
		}
	},
	}).mount('#app');
  </script>

</body>

</html>
```
# 0503
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
      padding: 1rem;
      font-size: 1rem;
    }

    h3 {
      margin-bottom: 1rem;
    }

    .wrap {
      position: relative;
      display: block;
      overflow: hidden;
    }

    .todo-lists,
    .done-lists {
      display: block;
      max-width: 150px;
      width: 45%;
      height: 120px;
      margin-right: 4%;
      float: left;
      border: 1px solid #ccc;
      padding: 1rem;
    }

    li {
      margin-bottom: 5px;
    }
  </style>
</head>

<body>

  <div id="app">
	  <div class="wrap">
		<div class="todo-lists">
		  <h3>Todo List</h3>
		  <ul>
			<li v-for="i in todoLists">
			  <label><input v-model="i.isDone" type="checkbox"> {{ i.title }}</label>
			</li>
		  </ul>
		</div>

		<div class="done-lists">
		  <h3>Done List</h3>
		  <ul>
			<li v-for="i in doneLists">
			  <label><input v-model="i.isDone" type="checkbox"> {{ i.title }}</label>
			</li>
		  </ul>
		</div>
	  </div>
  </div>
  
  <script src="https://unpkg.com/vue@next"></script>
  <script>
	  const vm = Vue.createApp({
	  data() {
		return {
		  lists: [{
			  id: 'task001',
			  title: '選項 1',
			  isDone: false
			},
			{
			  id: 'task002',
			  title: '選項 2',
			  isDone: false
			},
			{
			  id: 'task003',
			  title: '選項 3',
			  isDone: false
			},
		  ]
		}
	  },
	  computed: {
		todoLists() {
		  return this.lists.filter(d => !d.isDone)
		},
		doneLists() {
		  return this.lists.filter(d => d.isDone)
		},
	  }
	}).mount('#app');
  </script>

</body>

</html>
```
# 0506


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
      padding: 1rem;
      font-size: 1rem;
    }

    h3 {
      margin-bottom: 1rem;
    }

    .wrap {
      position: relative;
      display: block;
      overflow: hidden;
    }

    .todo-lists,
    .done-lists {
      display: block;
      max-width: 150px;
      width: 45%;
      height: 120px;
      margin-right: 4%;
      float: left;
      border: 1px solid #ccc;
      padding: 1rem;
    }

    li {
      margin-bottom: 5px;
    }
  </style>
</head>

<body>

  <div id="app">
	  <div id="app">
	<ul class="pagination">
	<li class="page-item" v-for="(page,key) in arr">
		<a class="page"> {{page}} </a>
	</li>

	</ul>
  </div>
  </div>
  
  <script src="https://unpkg.com/vue@next"></script>
  <script>
    const vm = Vue.createApp({
		data(){
			return {
			arr:{
				1:'Information Engineering Dept',
				2:'-----------',
				3:'Mechanical Engineering Dept',
				4:'-----------',
				5:'Information Manaagement Dept',
				6:'-----------',
			}
		}
	},
	}).mount('#app');
  </script>

</body>

</html>
```
# 0509
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
	<ul>
		<li v-for="(val, key) in book">{{ key }}_{{ val }}</li>
	</ul>
		<span v-for="(val, key) in book">+{{ key }}_{{ val }}	</span>
  </div>
 
  
  <script src="https://unpkg.com/vue@next"></script>
  <script>
    const vm = Vue.createApp({
		data(){
			return {
			book:{
				id:'08js',
				text:'kuro',
				publishedat:'2019/09'
			}
		}
	}
	}).mount('#app');
  </script>

</body>

</html>
```
# 0510divfor
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
	<div v-for="(val, key) in book">
	<ul>
		<li> {{ key }}_{{ val }}</li>
	</ul>
		<span>+{{ key }}_{{ val }}	</span>
  </div>
 
  
  <script src="https://unpkg.com/vue@next"></script>
  <script>
    const vm = Vue.createApp({
		data(){
			return {
			book:{
				id:'08js',
				text:'kuro',
				publishedat:'2019/09'
			}
		}
	}
	}).mount('#app');
  </script>

</body>

</html>
```
# 0511template
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
	<template v-for="(val, key) in book">
	<ul>
		<li> {{ key }}_{{ val }}</li>
	</ul>
		<span>+{{ key }}_{{ val }}	</span>
	</template>
  </div>
 
  
  <script src="https://unpkg.com/vue@next"></script>
  <script>
    const vm = Vue.createApp({
		data(){
			return {
			book:{
				id:'08js',
				text:'kuro',
				publishedat:'2019/09'
			}
		}
	}
	}).mount('#app');
  </script>

</body>

</html>
```
