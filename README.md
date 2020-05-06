
# uniapp-输入框组

### 使用方式 -> 直接导入示例项目启动
### 插件位于components/group-input.vue


```
<template>
	<view>
		<div v-for="(item, index) in models" :key="item.id">
			<view class="multi">
				<view class="multi-view" style="width: 30%;">
					<input 
					@input="onChangeInput"
						class="multi-input " 
						type="text" 
						:placeholder="'姓名' + (index + 1)"
						v-model="item[0].model"
						>
				</view>
				<view style="width: 65%;">
					<input 
						type="number" 
						maxlength="11" 
						class="multi-input " 
						placeholder="11位手机号码"
						v-model="item[1].model"
						>
				</view>
			</view>
		</div>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				models: []
			}
		},
		props: {
			size: {
				type: Number,
				default: () => 4
			},
		},
		created() {
			this.initModel()
		},
		
		watch: {
			models: {
				immediate: true,
				deep: true,
				handler(newVal) {
					this.$emit('group', newVal)
				}
			},
			size:{
				immediate: true,
				handler(newVal) {
					this.initModel()
				}
			}
			
		},
		methods: {
			onChangeInput(e){
				console.log(e)
			},
			initModel(){
				let models = []
				for(let i = 1 ; i <= this.size ; i++){
					let item = [
						{
							id: i + '-' + 1,
							model: ''
						},
						{
							id: i + '-' + 2,
							model: ''
						},
					]
					models.push(item)
				}
				this.models = models
			}
		}
	}
</script>
```