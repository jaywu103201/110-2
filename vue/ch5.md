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
