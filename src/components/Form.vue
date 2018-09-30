<template>
    <div class="container">
        <div class="sample">
            <form>
        		<div class="progress">
					<div class="progress-bar" :style="progressWidth"></div>
				</div>
				<div>
					<app-input v-for="(obj, index) in info"
                               :key="index"
                               :name="obj.name"
                               :index="index"
                               :pattern="obj.pattern"
                               :value="obj.value"    
                               @input-triger="updateVal"
                               
                    >
	                </app-input>
				</div>
				<button class="btn btn-primary" 
                        :disabled="this.done < this.info.length"
                        @click.prevent="onSend">
					{{ btnText }}
				</button>
			</form>
            <table class="table table-bordered">
                <tbody>
                    <app-result v-for="(obj, index) in info"
                                :key="index"
                                :name="obj.name"
                                :value="obj.value"
                    >
                    </app-result>
                </tbody>
            </table>
		</div>
    </div>
</template>

<script>
    import AppInput from './Input.vue';
    import AppResult from './Result.vue';

    import {mapGetters} from 'vuex';

    export default {
        computed: {
            ...mapGetters([
                'info'
            ]),
            progressWidth(){
				return {
					width: (this.done / this.info.length * 100) + '%'
				}
			},
        },
        data() {
            return {
                controls: [],
                done: 0,
                btnText: 'Send Data'
            };
        },
        methods: {
            updateVal(data) {
                this.$store.commit('updateVal', data);

                this.controls[data.index] = data.valid;

				let done = 0;

				for(let i = 0; i < this.controls.length; i++){
					if(this.controls[i]){
						done++;
					}
				}

                this.done = done;
            },
            onSend() {
                this.btnText = 'sending';

                setTimeout(() => {
                    this.btnText = 'send';
                }, 1000);
            }
        },
        components: {
            AppInput,
            AppResult,
        },
        created(){
			for(let i = 0; i < this.info.length; i++){
				this.controls.push(false);
			}
		},
    }
</script>

<style>

</style>

