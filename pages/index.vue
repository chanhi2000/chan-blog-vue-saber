<template>
	<div>
		<h1>My blog</h1>
		<p>
			This is my lovely (not yet) homepage!
			<saber-link to="/another">Another</saber-link>
		</p>

		<div>
			<Navbar/>
			<slot name="default"/>
			<div class="recent-posts" v-if="page.posts">
				<ui>
					<li v-for="post in page.posts" :key="post.permalink">
						<h2>
							{{ formatDate(post.createdAt) }}
							<saber-link :to="post.permalink">
								{{ post.title }}
							</saber-link>
						</h2>
					</li>
				</ui>
			</div>
		</div>
	</div>
</template>

<script>
export const data = {
	layout: 'page',
	injectAllPosts: true
}

export default {
	props: ['page'],
	methods: {
		formatDate(v) {
			const date = new Date(v)
			return `${date.getFullYear()}/${date.getMonth()+1}/${date.getDate()}`
		}
	}
}
</script>