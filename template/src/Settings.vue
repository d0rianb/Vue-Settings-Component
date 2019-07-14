<template>
<div class="settings">
	<div class="icon" @click="toggleModal">
		<i class="material-icons">settings</i>
	</div>
	<transition name="fade">
		<div class="modal" v-show="isVisible" v-click-outside="toggleModal">
			<div class="content">
				<div class="card" v-for="option in json" :key="option.name">
					<div class="card-title">{{ option.name }}</div>
					<input class="card-input" :type="option.type" :value="option.value" step=".1">
				</div>
			</div>
			<div class="command-bar">
				<button type="button" name="cancel">Annuler</button>
				<button type="button" name="confirm">Valider</button>
			</div>
		</div>
	</transition>
</div>
</template>

<script>
import ClickOutside from 'vue-click-outside'

export default {
	name: 'settings',
	props: {
		json: [Object, Array]
	},
	data() {
		return {
			isVisible: false
		}
	},
	mounted() {
		this.popupItem = this.$el
	},
	methods: {
		toggleModal() {
			return this.$set(this, 'isVisible', !this.isVisible)
		}
	},
	directives: {
		ClickOutside
	}

}
</script>

<style lang="scss" scoped>
.settings {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: auto 0.75em;

    .icon {
        padding: 0.35em;
        cursor: pointer;
        user-select: none;
    }

    .modal {
        position: absolute;
        top: 50%;
        left: 50%;
        width: 60vw;
        max-height: 70vh;
        box-shadow: 1px 1px 2px 2px #e8e8e8;
        background-color: #efefef54;
        border-radius: 2px;
        font-size: 1em;
        transform: translate(-50%, -50%);

        .content {
            display: flex;
            flex-flow: column nowrap;
            padding: 1.75rem 2rem;
            min-height: 80%;

            .card {
                display: flex;
                flex-flow: row nowrap;
                flex: 1;
                justify-content: space-between;
                align-items: center;
                margin: 0.5em;
                padding: 0.15em;

                input {
                    min-height: 1.1em;
                    padding: 0.35em 0.1em;
                    font-size: 0.9em;
                    outline: none;
                    border: none;
                    background-color: transparent;
                    border-bottom: 1px solid #ddd;
                    overflow: hidden;
                    resize: none;
                }

                input[type="number"] {
                    width: 3em;
                }
            }
        }

        .command-bar {
            display: flex;
            flex-flow: row;
            justify-content: flex-end;
            align-items: center;
            height: 2em;
            min-height: 20%;

            button {
                -webkit-appearance: none;
                padding: 0.5em;
                margin: 0.5em 1em;
            }
        }
    }

    .fade-enter-active,
    .fade-leave-active {
        transition: opacity 0.2s ease;
    }

    .fade-enter,
    .fade-leave-to {
        opacity: 0;
    }

}
</style>
