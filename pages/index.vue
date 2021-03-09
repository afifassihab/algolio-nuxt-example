<template>
	<ais-instant-search
		:search-client="searchClient"
		index-name="instant_search"
	>
		<ais-search-box />
		<ais-stats />
		<ais-refinement-list attribute="brand" />
		<ais-hits>
			<template slot="item" slot-scope="{ item }">
				<p>
					<ais-highlight attribute="name" :hit="item" />
				</p>
				<p>
					<ais-highlight attribute="brand" :hit="item" />
				</p>
			</template>
		</ais-hits>
		<ais-pagination />
	</ais-instant-search>
</template>

<script>
import {
	AisInstantSearch,
	AisRefinementList,
	AisHits,
	AisHighlight,
	AisSearchBox,
	AisStats,
	AisPagination,
	createServerRootMixin,
} from "vue-instantsearch";
import algoliasearch from "algoliasearch/lite";

const searchClient = algoliasearch(
	"latency",
	"6be0576ff61c053d5f9a3225e2a90f76"
);

export default {
	components: {
		AisInstantSearch,
		AisRefinementList,
		AisHits,
		AisHighlight,
		AisSearchBox,
		AisStats,
		AisPagination,
	},
	data() {
		return {
			searchClient,
		};
	},
	head() {
		return {
			link: [
				{
					rel: "stylesheet",
					href:
						"https://cdn.jsdelivr.net/npm/instantsearch.css@7.3.1/themes/algolia-min.css",
				},
			],
		};
	},
};
</script>

<style>
</style>
