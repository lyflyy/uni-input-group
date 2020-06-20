<template>
	<view class="content">
		
		<view>
			<button type="default" @click="size += 1">add</button>
			<button type="default" @click="size -= 1">sub</button>
		</view>
		
		<groupInput :size="size" @group="linstenGroup"/>
		
		<view style="padding: 30rpx;">
			<div v-for="item in data" :key="item.id">
				<view style="font-size: 30rpx;">
					{{ item[0].model }} - {{ item[1].model }}
				</view>
			</div>
		</view>
		
	</view>
</template>

<script>
	
	import groupInput from '@/components/dynamic-group-input/dynamic-group-input.vue'
	
	export default {
		components: {
			groupInput
		},
		data() {
			return {
				data: [],
				size: 4
			}
		},
		onLoad() {

		},
		methods: {
			linstenGroup(e){
				this.data = e
			}
		}
	}
</script>

<style>
	
</style>
