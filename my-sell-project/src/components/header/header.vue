<template>
	<div class="header">
		<div class="content-wrapper">
			<div class="avatar" @click="testFn">
				<img :src="seller.avatar" alt="" width="64" height="64">
			</div>
			<div class="content">
				<div class="title">
					<span class="brand"></span>
					<span class="name">{{ seller.name }}</span>
				</div>
				<div class="description">
					{{ `${seller.description}/${seller.deliveryTime}分钟送达`}}
				</div>
				<div class="supports">
					<div class="supports_desc">
						<span class="icon discount"></span>
						<span class="text">8折</span>
					</div>
				</div>
			</div>
			<div class="support-count">
				<span class="count">{{ `${seller.supports && seller.supports.length}个` }}</span>
				<i class="icon-keyboard_arrow_right"></i>
			</div>
		</div>
		<div class="bulletin-wrapper">
			<span class="bulletin-title"></span>
			<span class="bulletin-text"></span>
			<i class="icon-keyboard_arrow_right"></i>
		</div>
		<div class="background">
			<img :src="seller.avatar" alt="" width="100%" height="100%">
		</div>
	</div>
</template>

<script>
	export default {
		props: {
			seller: {
				type: Object
			}
		},
		methods: {
			testFn: function() {
				console.log(this.seller.infos);
			}
		},
		created() {
			// console.log(this.seller);
		}
	}
</script>

<style lang="scss" scoped>
	@import '../../common/scss/mixin';
	// @import '../../common/scss/icon';
	
	.header {
		position: relative;
		background: rgba(7,17,27,.5);
		color: #fff;
		blur: 10px;
		overflow: hidden;
		.content-wrapper {
			position: relative;
			display: flex;
			padding: 24px 12px 18px 24px;
			font-size: 12px;
			.avatar {
				img {
					border-radius: 2px;
				}
			}
			.content {
				margin-left: 16px;
				.title {
					margin: 2px 0 8px;
					font-size: 16px;
					.brand {
						display: inline-block;
						vertical-align: top;
						width: 30px;
						height: 18px;
						@include bg-image('brand');
						background-size: 30px 18px;
						background-repeat: no-repeat;
					}
					.name {
						margin-left: 6px;
						font-size: 16px;
						line-height: 18px;
						font-weight: bold;
					}
				}
				.description{
					font-size: 12px;
					margin-bottom: 10px;
				}
				.supports {
					.icon {
						display: inline-block;
						vertical-align: top;
						width: 12px;
						height: 12px;
						margin-right: 4px;
						background-size: 100%;
						&.decrease {
							@include bg-image('decrease_1');
						}
						&.discount {
							@include bg-image('discount_1');
						}
						&.guarantee {
							@include bg-image('guarantee_1');
						}
						&.invoice {
							@include bg-image('invoice_1');
						}
						&.special {
							@include bg-image('special_1');
						}
					}
					.text {
						line-height: 12px;
						font-size: 10px;
					}
				}
			}
			.support-count {
				position: absolute;
				right: 12px;
				bottom: 18px;
				padding: 0 8px;
				height: 24px;
				line-height: 24px;
				border-radius: 14px;
				background-color: rgba(0,0,0,.2);
				text-align: center;
				.count {
					vertical-align: top;
					font-size: 10px;
				}
				.icon-keyboard_arrow_right {
					font-size: 10px;
					margin-left: 2px;
					line-height: 24px;
				}
			}
		}
		.background {
			position: absolute;
			top: 0;
			left: 0;
			z-index: -1;
			width: 100%;
			height: 100%;
			filter: blur(10px);
		}
	}
</style>