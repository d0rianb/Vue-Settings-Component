<template>
<div>
	<header>
		<div class="title">{{ title }}</div>
		<settings :json="config.settings"></settings>
	</header>
</div>
</template>

<script>
import Settings from './Settings'
import JSONConfig from './assets/config.json'

export default {
	name: 'app',
	components: {
		Settings
	},
	data() {
		return {
			title: 'Titre',
			config: JSONConfig
		}
	}
}
</script>

<style lang="scss">
*,
*::after,
*::before {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: 'Roboto';
    font-weight: 400;
    font-size: 2vh;
}

#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

header {
    display: flex;
    flex-flow: row;
    min-height: 2em;
    background-color: #eee;
    justify-content: space-between;
    box-shadow: 0 0 2px 2px #6b6b6b59;
}

.title {
    padding: 0.5em;
    font-size: 1.25em;
}
</style>
