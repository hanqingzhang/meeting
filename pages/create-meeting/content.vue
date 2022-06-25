<template>
  <view class="basic-content">
		<view class="base-info g-border-bottom">
			<uni-forms :modelValue="formData" :rules="rules" label-width="100rpx">
				<uni-row class="demo-uni-row" :gutter="30">
					<uni-col :span="13">
						<uni-forms-item required class="wide-label" label="会议主题:" name="theme">
							<uni-easyinput type="text" v-model="formData.theme" />
						</uni-forms-item>
					</uni-col>
					<uni-col :span="11">
						<uni-forms-item required label="会议类型:" name="type">
							<uni-data-select v-model="formData.type" :localdata="typeList" placeholder=" "></uni-data-select>
						</uni-forms-item>
					</uni-col>
				</uni-row>
				
				<uni-row class="demo-uni-row" :gutter="30">
					<uni-col :span="13">
						<uni-forms-item required class="wide-label" label="开始时间:" name="startTime">
							<uni-datetime-picker type="datetime" v-model="formData.startTime" placeholder=" " />
						</uni-forms-item>
					</uni-col>
					<uni-col :span="11">
						<uni-forms-item required label="结束时间:" name="endTime">
							<uni-datetime-picker type="datetime" v-model="formData.endTime" placeholder=" " />
						</uni-forms-item>
					</uni-col>
				</uni-row>
				
				
				<uni-row class="demo-uni-row" :gutter="30">
					<uni-col :span="13">
						<uni-forms-item required class="wide-label" label="报送议题截止时间:" name="topicsEndTime">
							<uni-datetime-picker type="datetime" v-model="formData.topicsEndTime" placeholder=" " />
						</uni-forms-item>
					</uni-col>
					<uni-col :span="11">
						<uni-forms-item required label="主持人:" name="host">
							<uni-easyinput type="text" v-model="formData.host" />
						</uni-forms-item>
					</uni-col>
				</uni-row>
				
				<uni-row class="demo-uni-row" :gutter="30">
					<uni-col :span="13">
						<uni-forms-item required class="wide-label" label="会议地点:" name="place">
							<uni-easyinput type="text" v-model="formData.place" />
						</uni-forms-item>
					</uni-col>
					<uni-col :span="11">
						<uni-forms-item required label="部门:" name="department">
							<uni-data-select v-model="formData.department" :localdata="departmentList" placeholder=" "></uni-data-select>
						</uni-forms-item>
					</uni-col>
				</uni-row>
			</uni-forms>
		</view>
		
		<view class="extra-info">
			<view>
				<uni-data-checkbox multiple selectedColor="#b42722" v-model="openReminder" :localdata="range"></uni-data-checkbox>
			</view>
			<view>
				<text>提醒时间设置：提前</text>
				<uni-easyinput class="g-mr6 g-ml6" style="width: 100rpx;display: inline-block;" type="text" v-model="advanceTime" />
				<text class="g-mr32">小时</text>
				
				<text>重复提醒时间：</text>
				<uni-easyinput class="g-mr6 g-ml6" style="width: 100rpx;display: inline-block;" type="text" v-model="repeatTime" />
				<text>小时</text>
			</view>
		</view>
		
		<view class="buttom-btn-wrapper g-justify-center">
			<view class="g-button primary g-mr32">保 存</view>
			<view class="g-button primary">退 出</view>
		</view>
  </view>
</template>
<script>
  export default {
    name: "basic-content",
    components: {},
    data(){
      return {
				formData: {
					theme: '', // 主题
					type: '',// 类型
					startTime: '', // 开始时间
					endTime: '', // 结束时间
					topicsEndTime: '', // 议题纸质时间
					host: '',// 主持人
					place: '', // 会议地点
					department: '', // 部门
				},
				// 校验规则
				rules: {
					theme: {
						rules: [{
							required: true,
							errorMessage: '姓名不能为空'
						}]
					},
					type: {
						rules: [{
							required: true,
							errorMessage: '年龄不能为空'
						}]
					}
				},
				typeList: [
					{value: 1, text: "类型1"},
					{value: 2, text: "类型2"},
					{value: 3, text: "类型3"},
				],
				departmentList: [
					{value: 1, text: "总裁办"},
					{value: 2, text: "人事部"},
					{value: 3, text: "市场部"},
				],
				openReminder: [],
				range: [{"value": 1,"text": "是否开启日程提醒相关人员添加议题与上传资料"	}],
				advanceTime: '',
				repeatTime: '',
			}
    },
    methods: {},
  };
</script>
<style lang="scss" scoped>
  .basic-content {
		padding: 8rpx;
		.base-info{
			padding: 25rpx 25rpx 0;
			::v-deep .uni-forms-item__label{
				width: 60rpx;
			}
			::v-deep .wide-label .uni-forms-item__label{
				width: 105rpx;
			}
			::v-deep .uni-forms-item__content{
				.uni-stat__select{
					padding: 0;
					width: 100%;
					&>uni-view{
						width: 100%;
					}
					.uni-select__input-text{
						width: 100%;
						&.uni-select__input-placeholder{
							color: #ccc;
						}
					}
				}
			}
		}
		.extra-info{
			padding: 22rpx 40rpx 0;
			.open-reminder{
				flex: 0;
				::v-deep .checklist-box{
					margin-right: 0;
				}
			}
		}
		.buttom-btn-wrapper{
			margin-top: 35rpx;
		}
  }
</style>