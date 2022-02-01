<template>
	<article class="tweet border-b border-gray-600">
		<router-link to="#" class="flex p-4">
			<figure class="w-16 mr-3">
				<img :src="tweet.author.profile_img_url" alt="Image" class="rounded-full w-full" />
			</figure>

			<section class="flex-1">
				<div>
					<span class="text-white font-bold">
						{{ tweet.author.display_name }}
					</span>
					<span class="text-gray-500 ml-2 font-normal">
						{{ tweet.author.username }}
					</span>
				</div>

				<div :class="(tweet.image ? 'mb-3' : '')">
					<p class="text-white" v-html="tweet.body"></p>
				</div>

				<figure v-if="tweet.image" class="rounded-xl border border-gray-600 overflow-hidden">
					<img 
						:src="tweet.image.url" 
						:alt="tweet.image.alt" 
						class="w-full h-44 object-cover" />
				</figure>

				<div class="mt-2 flex items-center justify-between">
					<div class="text-gray-500">
						<i class="fas fa-comment p-2 mr-1 rounded-full hover:bg-green-900 hover:text-green-500"></i>
						<span>{{ tweet.stats.comments.length }}</span>
					</div>
					<div class="text-gray-500">
						<i class="fas fa-retweet p-2 mr-1 rounded-full hover:bg-green-900 hover:text-green-500"></i>
						<span>{{ tweet.stats.retweets.length }}</span>
					</div>
					<div class="text-gray-500">
						<i class="fas fa-heart p-2 mr-1 rounded-full hover:bg-green-900 hover:text-green-500"></i>
						<span>{{ tweet.stats.likes.length }}</span>
					</div>
					<div class="text-gray-500">
						<i class="fas fa-share p-2 mr-1 rounded-full hover:bg-green-900 hover:text-green-500"></i>
					</div>
				</div>
			</section>
		</router-link>
	</article>
</template>

<script>
export default {
	props: ['tweet']
}
</script>