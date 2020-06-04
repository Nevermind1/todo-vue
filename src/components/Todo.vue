<template>
	<div>
		<input type="text" value="" 
		placeholder="what u want to do" 
		v-model="newTodo"
		@keyup.enter="addTodo"
		class="todo-input"/>
		<!-- <p>Todo list goes here</p> -->
		<div class="todos" v-for="(item,index) in todos" :key="item.id">
			<div v-if="!edited" @dblclick="todoEditing">
				{{item.title}}
			</div>
			<div v-else>
				<input type="text" value="" v-model="item.title"  @keyup.enter="escEdit"/>
			</div>
			<div class="remove-item" @click="remove(index)">
				&times;
			</div>
		</div>
	</div>
</template>

<script>
	export default{
		name:'Todo',
		data(){
			return{
				newTodo:'',
				idFortodo:3,
				todos:[
					{'id':1,'title':'Finish Vue Screencast','complete':false,edited:false,},
					{'id':2,'title':'Take over world','complete':false,edited:false,},
				]
			}
		},
		methods:{
			escEdit(index){
				// index.edited=!index.edited
				this.todos[index].edited=!this.todos[index].edited
			},
			todoEditing(index){
				this.edited=!this.edited
			},
			addTodo(){
				if(this.newTodo.trim().length==0){
					return
				}
				this.todos.push({
					id:this.idFortodo,
					title:this.newTodo,
					complete:false,
					edited:false,
				})
				this.newTodo=''
				this.idFortodo++
			},
			remove(index){
				this.todos.splice(index,1)
			}
		}
	}
</script>

<style scoped>
	.todo-input{
		width: 100%;
		padding: 10px 18px;
		font-size: 19px;
		margin-bottom: 16px;
		&:focus{
			outline: 0;
		}
	}
	.todos{
		margin-bottom: 12px;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	.remove-item{
		cursor: pointer;
		margin-left: 14px;
		margin-left: 14px;
		&:hover{
			color: black;
		}
	}
</style>
