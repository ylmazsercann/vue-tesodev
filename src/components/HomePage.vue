<template>
  <div>
    <div class="menu-icon" onclick="myFunction(this)">
            <div class="bar1"></div>
            <div class="bar2"></div>
            <div class="bar3"></div>
            </div>
        <div class="container">
             <div class="search-console">
                <a href="https://www.tesodev.com/" class="logo">
                    <img class="img-fluid" src="../assets/logo.jpg" alt="">
                </a>
                <h1>TESODEV Search Console</h1>
                 <form>
                    <div class="form-group">
                        <input type="text" class="form-control" v-model="Searching" name="search" placeholder="Search Name.." />
                    </div>
                 </form>
				 <transition-group tag="div" name="list-animation">
                 <div class="result photo-animated" v-for="search in filteredId" :key="search.item" >
                     <div class="result-table">
                         <div class="items">
                            <p><strong>{{ search.item }}</strong></p>
                            <p>{{ search.description }}</p>
                         </div>
                         <div class="created">
                            <p>Created By {{ search.created_by }}</p>
                         </div>
                    </div>
                    <div class="clear"></div>
                 </div>
				</transition-group>
            </div>
        </div>
  </div>
</template>

<script>
import products from '../../generated.json'
export default {
  data(){
    return {
		Searching: "",
		items: products
	}
  },
   computed: {
        
        filteredId: function () {
			
            var allitems = this.items;
            var Searching = this.Searching;

            if(!Searching){
                return allitems;
            }

            allitems = allitems.filter(function(data){
                if(data.item.toLowerCase().trim().indexOf(Searching) !== -1){
                    return data;
                }
            })

            return allitems;
        }
	 }
  
}
</script>

<style scoped lang="less">
* {
	padding: 0;
	margin: 0;
	box-sizing: border-box;
	outline: 0;
}
.clear {
	clear: both;
}
#app {
  font-family: 'Baloo Tammudu 2', cursive;
}
.menu-icon {
	position: fixed;
	width: 75px;
	background-color: red;
	min-height: 100vh;
	background-color: #90badc;
	padding-top: 20px;
}
.bar1 {
	width: 35px;
	height: 5px;
	background-color: #737779;
	margin: 6px auto;
	transition: 0.4s;
	border-radius: 25%;
}
.bar2 {
	width: 35px;
	height: 5px;
	background-color: #737779;
	margin: 6px auto;
	transition: 0.4s;
	border-radius: 25%;
}
.bar3 {
	width: 35px;
	height: 5px;
	background-color: #737779;
	margin: 6px auto;
	transition: 0.4s;
	border-radius: 25%;
}
.change {
	.bar1 {
		-webkit-transform: rotate(-45deg) translate(-9px, 6px);
		-moz-transform: rotate(-45deg) translate(-9px, 6px);
		-ms-transform: rotate(-45deg) translate(-9px, 6px);
		-o-transform: rotate(-45deg) translate(-9px, 6px);
		transform: rotate(-45deg) translate(-9px, 6px);
	}
	.bar2 {
		opacity: 0;
	}
	.bar3 {
		-webkit-transform: rotate(45deg) translate(-8px, -8px);
		-moz-transform: rotate(45deg) translate(-8px, -8px);
		-ms-transform: rotate(45deg) translate(-8px, -8px);
		-o-transform: rotate(45deg) translate(-8px, -8px);
		transform: rotate(45deg) translate(-8px, -8px);
	}
}
.container {
	margin-left: 75px;
}
.search-console {
	padding-top: 50px;
	width: 100%;
	text-align: center;
}
.logo {
	img {
		width: 100%;
		height: auto;
		max-width: 300px;
		padding: 0 20px;
	}
}
h1 {
	font-size: 20px;
	font-weight: 500;
	margin:20px 0;
}
input[type=text] {
	width: 320px;
	box-sizing: border-box;
	border: 2px solid #ccc;
	border-radius: 4px;
	font-size: 16px;
	background-color: #e5e5e5;
	background-image: url('/src/assets/searchicon.png');
	background-position: 10px 15px;
	background-repeat: no-repeat;
	padding: 20px 20px 20px 40px;
	-webkit-transition: width 0.4s ease-in-out;
	-moz-transition: width 0.4s ease-in-out;
	-ms-transition: width 0.4s ease-in-out;
	-o-transition: width 0.4s ease-in-out;
	transition: width 0.4s ease-in-out;
	&:focus {
		width: 330px;
		border: 2px solid green;
	}
}
.result {
	margin: 20px auto;
	width: 100%;
	max-width: 900px;
	border-radius: 20px;
	background-color: #e5e5e5;
	color: #737779;
	text-align: left;
	font-size: 16px;
	font-weight: 500;
}
.result-table {
	padding: 10px 20px;
}
.items {
	float: left;
	max-width: 75%;
	p+p {
		padding-left: 5px;
	}
}
.created {
	float: right;
	line-height: 70px;
}
@media (min-width: 320px) and (max-width: 424px) {
	input[type=text] {
		width: 180px;
		&:focus {
			width: 220px;
			border: 2px solid green;
		}
	}
}
@media (min-width: 425px) and (max-width: 767px) {
	input[type=text] {
		width: 300px;
		&:focus {
			width: 320px;
			border: 2px solid green;
		}
	}
}
@media (max-width: 768px) {
	.result {
		margin: 15px;
		max-width: 90%;
		height: auto;
	}
	.items {
		float: none;
		max-width: none;
		p+p {
			padding: 10px 0;
		}
	}
	.created {
		float: none;
		line-height: normal;
	}
}
@media (max-width: 424px) {
	.result {
		max-width: 88%;
	}
	.result-table {
		font-size: 14px;
	}
}
.list-animation-enter, .list-animation-leave-to {
	opacity: 0;
	transform: translateY(30px);
}

.list-animation-leave-active {
	position: absolute;
}
.photo-animated {
	transition: all 0.5s;
}
</style>
