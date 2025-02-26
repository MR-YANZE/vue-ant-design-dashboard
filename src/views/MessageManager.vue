<template>
	<div>
		<a-card :bordered="false" class="header-solid h-full" :bodyStyle="{ padding: 0, }">
			<!-- 标题 -->
			<template #title>
				<a-row type="flex" align="middle">
					<a-col :span="24" :md="20">
						<h5 class="font-semibold m-0">
							消息管理
						</h5>
					</a-col>
					<a-col :span="24" :md="4" style="display: flex; align-items: center; justify-content: flex-end">
						<a-input-search class="header-search" :class="searchLoading ? 'loading' : ''"
							placeholder="输入关键词" @search="onSearch" :loading='searchLoading'>
						</a-input-search>
					</a-col>
				</a-row>
			</template>

			<!-- 表格 -->
			<a-table :columns="tableColumns" :data-source="tableData" :pagination="false">

				<template slot="author" slot-scope="author">
					<div class="table-avatar-info">
						<a-avatar shape="square" :src="author.avatar" />
						<div class="avatar-info">
							<h6>{{ author.name }}</h6>
							<p>{{ author.email }}</p>
						</div>
					</div>
				</template>

				<template slot="func" slot-scope="func">
					<div class="author-info">
						<h6 class="m-0">{{ func.job }}</h6>
						<p class="m-0 font-regular text-muted">{{ func.department }}</p>
					</div>
				</template>

				<template slot="status" slot-scope="status">
					<a-tag class="tag-status" :class="status ? 'ant-tag-primary' : 'ant-tag-muted'">
						{{ status ? "ONLINE" : "OFFLINE" }}
					</a-tag>
				</template>

				<template slot="editBtn" slot-scope="row">
					<a-button type="link" :data-id="row.key" class="btn-edit">
						Edit
					</a-button>
				</template>
			</a-table>

			<!-- 分页 -->
			<a-pagination v-model="current" :total="500" show-less-items style="text-align: right; margin: 16px 20px 16px 0;"/>
		</a-card>
	</div>
</template>

<script>

// "Authors" table list of columns and their properties.
const tableColumns = [
	{
		title: 'AUTHOR',
		dataIndex: 'author',
		scopedSlots: { customRender: 'author' },
	},
	{
		title: 'FUNCTION',
		dataIndex: 'func',
		scopedSlots: { customRender: 'func' },
	},
	{
		title: 'STATUS',
		dataIndex: 'status',
		scopedSlots: { customRender: 'status' },
	},
	{
		title: 'EMPLOYED',
		dataIndex: 'employed',
		class: 'text-muted',
	},
	{
		title: '',
		scopedSlots: { customRender: 'editBtn' },
		width: 50,
	},
];

// "Authors" table list of rows and their properties.
const tableData = [
	{
		key: '1',
		author: {
			avatar: 'images/face-2.jpg',
			name: 'Michael John',
			email: 'michael@mail.com',
		},
		func: {
			job: 'Manager',
			department: 'Organization',
		},
		status: 1,
		employed: '23/04/18',
	},
	{
		key: '2',
		author: {
			avatar: 'images/face-3.jpg',
			name: 'Alexa Liras',
			email: 'alexa@mail.com',
		},
		func: {
			job: 'Programator',
			department: 'Developer',
		},
		status: 0,
		employed: '23/12/20',
	},
	{
		key: '3',
		author: {
			avatar: 'images/face-1.jpg',
			name: 'Laure Perrier',
			email: 'laure@mail.com',
		},
		func: {
			job: 'Executive',
			department: 'Projects',
		},
		status: 1,
		employed: '13/04/19',
	},
	{
		key: '4',
		author: {
			avatar: 'images/face-4.jpg',
			name: 'Miriam Eric',
			email: 'miriam@mail.com',
		},
		func: {
			job: 'Marketing',
			department: 'Organization',
		},
		status: 1,
		employed: '03/04/21',
	},
	{
		key: '5',
		author: {
			avatar: 'images/face-5.jpeg',
			name: 'Richard Gran',
			email: 'richard@mail.com',
		},
		func: {
			job: 'Manager',
			department: 'Organization',
		},
		status: 0,
		employed: '23/03/20',
	},
	{
		key: '6',
		author: {
			avatar: 'images/face-6.jpeg',
			name: 'John Levi',
			email: 'john@mail.com',
		},
		func: {
			job: 'Tester',
			department: 'Developer',
		},
		status: 0,
		employed: '14/04/17',
	},
];

export default ({
	components: {
	},
	data() {
		return {
			// Associating "Authors" table data with its corresponding property.
			tableColumns: tableColumns,

			// Associating "Authors" table columns with its corresponding property.
			tableData: tableData,
			current: 6,
		}
	},
})

</script>

<style lang="scss"></style>