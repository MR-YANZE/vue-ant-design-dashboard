<template>
	<component :is="navbarFixed ? 'a-affix' : 'div'" :offset-top="top">
		<a-layout-header>
			<a-row type="flex">

				<a-col :span="24" :md="6">

					<!-- 顶部面包屑 -->
					<a-breadcrumb>
						<a-breadcrumb-item><router-link to="/"> 页面</router-link></a-breadcrumb-item>
						<a-breadcrumb-item>{{ this.$route.name }}</a-breadcrumb-item>
					</a-breadcrumb>

					<!-- 顶部页面标题 -->
					<!-- <div class="ant-page-header-heading">
						<span class="ant-page-header-heading-title">{{ this.$route.name }}</span>
					</div> -->

				</a-col>

				<a-col :span="24" :md="18" class="header-control">
					<!-- 顶部退出按钮 -->
					<router-link to="/sign-in" class="btn-sign-in" @click="e => e.preventDefault()">
						<svg width="20" height="20" fill="none" viewBox="0 0 1024 1024"
							xmlns="http://www.w3.org/2000/svg">
							<path fill-rule="evenodd" clip-rule="evenodd"
								d="M767.986697 174.60776c29.986965 21.286816 56.608276 45.414329 79.868025 72.355935 23.316032 26.970258 43.268456 56.087413 59.914578 87.349417 16.647145 31.29168 29.291117 64.381309 37.932937 99.326193s12.991895 70.355371 12.991895 106.316397c0 61.887512-11.83249 119.945813-35.43914 174.176948-23.663956 54.231135-55.565527 101.501742-95.875604 141.754514-40.252773 40.252773-87.466074 72.181973-141.753491 95.818299-54.172807 23.635303-112.289436 35.438117-174.176948 35.438117-61.191664 0-118.90204-11.802814-173.191504-35.438117-54.172807-23.636327-101.617375-55.565527-142.218072-95.818299-40.600697-40.281425-72.501244-87.523379-95.817276-141.754514-23.317055-54.231135-34.917254-112.289436-34.917254-174.176948 0-35.265178 4.117784-69.891813 12.412704-103.821577 8.352225-33.930787 20.184715-66.207911 35.496445-96.833419 15.311731-30.594809 34.220383-59.21873 56.840566-85.841064 22.620184-26.623357 47.90915-50.576909 75.865875-71.863724 14.674211-10.643408 30.507828-14.645558 47.444569-11.977799 16.935718 2.667759 30.740118 10.962679 41.412179 24.941042 10.67206 13.977339 14.616906 29.609365 12.006452 46.922682-2.667759 17.313318-10.961656 31.29168-24.998347 41.934065-41.87676 30.595832-74.009597 68.209498-96.281857 112.783693-22.272259 44.602847-33.466206 92.510974-33.466206 143.755078 0 43.906999 8.293897 85.34783 24.998347 124.267235 16.587793 38.948057 39.382962 72.878844 68.325132 101.821013 29.000498 28.942169 62.872956 51.9113 101.849666 68.876694 38.918381 16.965393 80.331583 25.433252 124.238582 25.433252 43.964304 0 85.377506-8.467859 124.295887-25.433252s72.849168-39.933501 101.849666-68.876694c28.942169-28.942169 51.852972-62.872956 68.847018-101.821013 16.994046-38.918381 25.461905-80.359212 25.461905-124.267235 0-51.9113-12.005428-100.979856-35.961026-147.235342-23.953551-46.25651-57.537438-84.362386-100.805894-114.291023-14.615882-9.976212-23.431665-23.635303-26.448372-40.918945-3.015683-17.313318 0.521886-33.293267 10.498098-47.938825 9.976212-13.977339 23.606651-22.446221 40.891316-25.433252C737.420541 161.121608 753.370815 164.631548 767.986697 174.60776L767.986697 174.60776 767.986697 174.60776 767.986697 174.60776zM511.44895 542.942733c-17.284665 0-32.075533-6.148024-44.428885-18.473747-12.297071-12.296047-18.444071-27.115568-18.444071-44.428885L448.575993 100.742449c0-17.313318 6.148024-32.277124 18.444071-44.921095 12.353352-12.642948 27.14422-18.965957 44.428885-18.965957 17.97949 0 33.118282 6.323009 45.414329 18.965957 12.354376 12.643971 18.502399 27.607778 18.502399 44.921095l0 379.297652c0 17.313318-6.148024 32.132838-18.502399 44.428885C544.567231 536.795732 529.42844 542.942733 511.44895 542.942733L511.44895 542.942733 511.44895 542.942733 511.44895 542.942733zM511.44895 542.942733"
								fill="#000000"></path>
						</svg>
					</router-link>

					<!-- 顶部消息通知 -->
					<a-dropdown overlayClassName="header-notifications-dropdown" :getPopupContainer="() => wrapper">

						<router-link to="/messageManager" @click="e => e.preventDefault()">
							<a-badge count="4">
								<a class="ant-dropdown-link">
									<svg width="20" height="20" viewBox="0 0 20 20" fill="none"
										xmlns="http://www.w3.org/2000/svg">
										<path
											d="M10 2C6.68632 2 4.00003 4.68629 4.00003 8V11.5858L3.29292 12.2929C3.00692 12.5789 2.92137 13.009 3.07615 13.3827C3.23093 13.7564 3.59557 14 4.00003 14H16C16.4045 14 16.7691 13.7564 16.9239 13.3827C17.0787 13.009 16.9931 12.5789 16.7071 12.2929L16 11.5858V8C16 4.68629 13.3137 2 10 2Z"
											fill="#111827" />
										<path d="M10 18C8.34315 18 7 16.6569 7 15H13C13 16.6569 11.6569 18 10 18Z"
											fill="#111827" />
									</svg>
								</a>
							</a-badge>
						</router-link>

						<a-list item-layout="horizontal" class="header-notifications-list"
							:data-source="notificationsData" slot="overlay">
							<a-list-item slot="renderItem" slot-scope="item">
								<a-list-item-meta>
									<template #description>
										<svg width="20" height="20" viewBox="0 0 20 20" fill="none"
											xmlns="http://www.w3.org/2000/svg">
											<path fill-rule="evenodd" clip-rule="evenodd"
												d="M10 18C14.4183 18 18 14.4183 18 10C18 5.58172 14.4183 2 10 2C5.58172 2 2 5.58172 2 10C2 14.4183 5.58172 18 10 18ZM11 6C11 5.44772 10.5523 5 10 5C9.44772 5 9 5.44772 9 6V10C9 10.2652 9.10536 10.5196 9.29289 10.7071L12.1213 13.5355C12.5118 13.9261 13.145 13.9261 13.5355 13.5355C13.9261 13.145 13.9261 12.5118 13.5355 12.1213L11 9.58579V6Z"
												fill="#111827" />
										</svg>
										<span>{{ item.time }}</span>
									</template>
									<a slot="title" href="#">{{ item.title }}</a>
									<a-avatar v-if="item.img" slot="avatar" shape="square" :src="item.img" />
									<a-avatar v-else shape="square" slot="avatar" v-html="item.svg" />
								</a-list-item-meta>
							</a-list-item>
						</a-list>
					</a-dropdown>

					<!-- 顶部设置按钮 -->
					<a-button type="link" ref="secondarySidebarTriggerBtn" @click="$emit('toggleSettingsDrawer', true)">
						<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path fill-rule="evenodd" clip-rule="evenodd"
								d="M11.4892 3.17094C11.1102 1.60969 8.8898 1.60969 8.51078 3.17094C8.26594 4.17949 7.11045 4.65811 6.22416 4.11809C4.85218 3.28212 3.28212 4.85218 4.11809 6.22416C4.65811 7.11045 4.17949 8.26593 3.17094 8.51078C1.60969 8.8898 1.60969 11.1102 3.17094 11.4892C4.17949 11.7341 4.65811 12.8896 4.11809 13.7758C3.28212 15.1478 4.85218 16.7179 6.22417 15.8819C7.11045 15.3419 8.26594 15.8205 8.51078 16.8291C8.8898 18.3903 11.1102 18.3903 11.4892 16.8291C11.7341 15.8205 12.8896 15.3419 13.7758 15.8819C15.1478 16.7179 16.7179 15.1478 15.8819 13.7758C15.3419 12.8896 15.8205 11.7341 16.8291 11.4892C18.3903 11.1102 18.3903 8.8898 16.8291 8.51078C15.8205 8.26593 15.3419 7.11045 15.8819 6.22416C16.7179 4.85218 15.1478 3.28212 13.7758 4.11809C12.8896 4.65811 11.7341 4.17949 11.4892 3.17094ZM10 13C11.6569 13 13 11.6569 13 10C13 8.34315 11.6569 7 10 7C8.34315 7 7 8.34315 7 10C7 11.6569 8.34315 13 10 13Z"
								fill="#111827" />
						</svg>
					</a-button>

					<!-- <a-button type="link" class="sidebar-toggler" @click="$emit('toggleSidebar', ! sidebarCollapsed) , resizeEventHandler()">
						<svg width="20" height="20" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><path d="M16 132h416c8.837 0 16-7.163 16-16V76c0-8.837-7.163-16-16-16H16C7.163 60 0 67.163 0 76v40c0 8.837 7.163 16 16 16zm0 160h416c8.837 0 16-7.163 16-16v-40c0-8.837-7.163-16-16-16H16c-8.837 0-16 7.163-16 16v40c0 8.837 7.163 16 16 16zm0 160h416c8.837 0 16-7.163 16-16v-40c0-8.837-7.163-16-16-16H16c-8.837 0-16 7.163-16 16v40c0 8.837 7.163 16 16 16z"/></svg>
					</a-button> -->

					<!-- 顶部登录按钮 -->
					<!-- <router-link to="/sign-in" class="btn-sign-in" @click="e => e.preventDefault()">
						<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path fill-rule="evenodd" clip-rule="evenodd" d="M18 10C18 14.4183 14.4183 18 10 18C5.58172 18 2 14.4183 2 10C2 5.58172 5.58172 2 10 2C14.4183 2 18 5.58172 18 10ZM12 7C12 8.10457 11.1046 9 10 9C8.89543 9 8 8.10457 8 7C8 5.89543 8.89543 5 10 5C11.1046 5 12 5.89543 12 7ZM9.99993 11C7.98239 11 6.24394 12.195 5.45374 13.9157C6.55403 15.192 8.18265 16 9.99998 16C11.8173 16 13.4459 15.1921 14.5462 13.9158C13.756 12.195 12.0175 11 9.99993 11Z" fill="#111827"/>
						</svg>
						<span>Sign In</span>
					</router-link> -->

					<!-- 顶部搜索框 -->
					<!-- <a-input-search class="header-search" :class="searchLoading ? 'loading' : ''" placeholder="Type here…" @search="onSearch" :loading='searchLoading'>
						<svg slot="prefix" width="16" height="16" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path fill-rule="evenodd" clip-rule="evenodd" d="M8 4C5.79086 4 4 5.79086 4 8C4 10.2091 5.79086 12 8 12C10.2091 12 12 10.2091 12 8C12 5.79086 10.2091 4 8 4ZM2 8C2 4.68629 4.68629 2 8 2C11.3137 2 14 4.68629 14 8C14 9.29583 13.5892 10.4957 12.8907 11.4765L17.7071 16.2929C18.0976 16.6834 18.0976 17.3166 17.7071 17.7071C17.3166 18.0976 16.6834 18.0976 16.2929 17.7071L11.4765 12.8907C10.4957 13.5892 9.29583 14 8 14C4.68629 14 2 11.3137 2 8Z" fill="#111827"/>
						</svg>
					</a-input-search> -->
				</a-col>

			</a-row>
		</a-layout-header>
	</component>
</template>

<script>

const notificationsData = [
	{
		title: 'New message from Sophie',
		img: 'images/face-1.jpg',
		time: '13 minutes ago',
	},
	{
		title: 'New album by Travis Scott',
		svg: `<svg width="20" height="20" viewBox="0 0 107 107" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
					<title>logo-spotify</title>
					<g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
						<g id="logo-spotify" fill="#2EBD59" fill-rule="nonzero">
							<path d="M53.5,0 C23.9517912,0 0,23.9517912 0,53.5 C0,83.0482088 23.9517912,107 53.5,107 C83.0482088,107 107,83.0482088 107,53.5 C107,23.9554418 83.0482088,0.00365063118 53.5,0 Z M78.0358922,77.1597407 C77.0757762,78.7368134 75.0204708,79.2296486 73.4506994,78.2695326 C60.8888775,70.5922552 45.0743432,68.8582054 26.4524736,73.1111907 C24.656363,73.523712 22.8675537,72.3993176 22.458683,70.6032071 C22.0461617,68.8070966 23.1669055,67.0182873 24.9666667,66.6094166 C45.3444899,61.9548618 62.8273627,63.9590583 76.9297509,72.5745479 C78.4995223,73.5419652 78.9996588,75.5899693 78.0358922,77.1597407 L78.0358922,77.1597407 Z M84.5814739,62.5973729 C83.373115,64.5614125 80.8030706,65.1747185 78.8426817,63.9700102 C64.4664961,55.1318321 42.5408052,52.5727397 25.5325145,57.7347322 C23.3275333,58.4027977 20.9984306,57.1579324 20.3267144,54.9566018 C19.6622996,52.7516206 20.9071648,50.4261685 23.1084954,49.7544524 C42.5371546,43.858683 66.6933811,46.7134766 83.2051859,56.8622313 C85.1692255,58.0705902 85.7898328,60.636984 84.5814739,62.5973729 Z M85.1436711,47.4253497 C67.8980894,37.1853292 39.4523712,36.2434664 22.9880246,41.2375299 C20.3449676,42.0406687 17.5485841,40.5475606 16.7490959,37.9045036 C15.9496076,35.2614466 17.4390652,32.4650631 20.0857728,31.6619243 C38.9850904,25.9267827 70.3987718,27.0329239 90.2509041,38.8171614 C92.627465,40.2299556 93.4087001,43.3001365 91.9995565,45.6730467 C90.5940635,48.0532583 87.5165814,48.838144 85.1436711,47.4253497 Z" id="Shape"></path>
						</g>
					</g>
				</svg>`,
		time: '1 day ago',
	},
	{
		title: 'Payment completed',
		svg: `<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
					<path fill="#1890FF" d="M4 4C2.89543 4 2 4.89543 2 6V7H18V6C18 4.89543 17.1046 4 16 4H4Z"/>
					<path fill="#1890FF" fill-rule="evenodd" clip-rule="evenodd" d="M18 9H2V14C2 15.1046 2.89543 16 4 16H16C17.1046 16 18 15.1046 18 14V9ZM4 13C4 12.4477 4.44772 12 5 12H6C6.55228 12 7 12.4477 7 13C7 13.5523 6.55228 14 6 14H5C4.44772 14 4 13.5523 4 13ZM9 12C8.44772 12 8 12.4477 8 13C8 13.5523 8.44772 14 9 14H10C10.5523 14 11 13.5523 11 13C11 12.4477 10.5523 12 10 12H9Z"/>
				</svg>`,
		time: '2 days ago',
	},
];

export default ({
	props: {
		// Header fixed status.
		navbarFixed: {
			type: Boolean,
			default: false,
		},

		// Sidebar collapsed status.
		sidebarCollapsed: {
			type: Boolean,
			default: false,
		},

		// Header notifications data.
		notificationsData: {
			type: Array,
			default: () => notificationsData,
		},
	},
	data() {
		return {
			// Fixed header/sidebar-footer ( Affix component ) top offset.
			top: 0,

			// Search input loading status.
			searchLoading: false,

			// The wrapper element to attach dropdowns to.
			wrapper: document.body,
		}
	},
	methods: {
		resizeEventHandler() {
			this.top = this.top ? 0 : -0.01;
			// To refresh the header if the window size changes.
			// Reason for the negative value is that it doesn't activate the affix unless
			// scroller is anywhere but the top of the page.
		},
		onSearch(value) {
		}
	},
	mounted: function () {
		// Set the wrapper to the proper element, layout wrapper.
		this.wrapper = document.getElementById('layout-dashboard');
	},
	created() {
		// Registering window resize event listener to fix affix elements size
		// error while resizing.
		window.addEventListener("resize", this.resizeEventHandler);
	},
	destroyed() {
		// Removing window resize event listener.
		window.removeEventListener("resize", this.resizeEventHandler);
	},
})

</script>
