<template>
  <div class="app-container">
    <!-- 顶部 Header 区域 -->
    <mt-header fixed title="陈独秀&杨超越.Vue项目"></mt-header>

    <!-- 中间路由 router-view 区域 -->
		<transition>
			<router-view></router-view>
		</transition>
		

    <!-- 底部 Tabbar 区域 -->
    <nav class="mui-bar mui-bar-tab">
			<router-link class="mui-tab-item" to="/home">
				<span class="mui-icon mui-icon-home"></span>
				<span class="mui-tab-label">首页</span>
			</router-link>
			<router-link class="mui-tab-item" to="member">
				<span class="mui-icon mui-icon-contact"></span>
				<span class="mui-tab-label">会员</span>
			</router-link>
			<router-link class="mui-tab-item" to="shopcar">
				<span class="mui-icon mui-icon-extra mui-icon-extra-cart">
					<span class="mui-badge">9</span>
				</span>
				<span class="mui-tab-label">购物车</span>
			</router-link>
			<router-link class="mui-tab-item" to="/search">
				<span class="mui-icon mui-icon-gear"></span>
				<span class="mui-tab-label">搜索</span>
			</router-link>
		</nav>

  </div>
</template>

<script>

</script>


<style lang="scss" scoped>
		.app-container {
		padding-top: 40px;
		padding-bottom: 50px;
		overflow-x: hidden;

		.v-enter {
			transform: translateX(100%);
			opacity: 0;
		}

		.v-leave-to {
			position: absolute;
			transform: translateX(-100%);
			opacity: 0;
		}

		.v-enter-active,
		.v-leave-active {
			transition: all 0.6s ease;
		}
	}
</style>




