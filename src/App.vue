<template>
	<transition name="fade" tag="div" class="wrapper" mode="out-in">
		<div class="wrapper" id="user-title">
			<LandingPage :name="user.name" :status="user.status" />
			<Description :user="user" :content="about" :links="links" />
			<Experience :content="experiences" />
			<Skills :content="skills" />
			<Footer :user="user" :links="links" />
		</div>
	</transition>
</template>

<script>
	import LandingPage from "./components/LandingPage.vue";
	import Description from "./components/Description.vue";
	import Experience from "./components/Experience.vue";
	import Skills from "./components/Skills.vue";
	import Footer from "./components/Footer.vue";

	import { userData, aboutData, linksData, experiencesData, skillsData } from './data/user.js';
	
	export default {
		name: "App",
		components: {
			LandingPage,
			Description,
			Experience,
			Skills,
			Footer,
		},
		data: () => ({
			isLoaded: true,
			user: userData,
			about: aboutData,
			links: linksData,
			experiences: experiencesData,
			skills: skillsData
		}),
		methods: {
			findSlug(slug) {
				return this.posts.find((item) => {
					return item.slug === slug;
				});
			}
		}
	};
</script>

<style scoped lang="scss">
	@import "@/styles/constants.scss";

	#user-title {
		font-family: Montserrat-Regular, serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		color: #2c3e50;
	}

	.wrapper {
		height: 100%;
	}
</style>
