<template>
    <div class="form-group">
        <label>{{ name }}</label>
        <span class="fa" :class="validClass" v-if="activated">
        </span>
        <input type="text" 
        	   class="form-control"
               :value="value"
               @input="sendVal"
        >
    </div>
</template>

<script>
    export default {
        props: ['name', 'pattern', 'value', 'index'],
        data() {
            return {
                activated: this.value != ''
            };
        },
        computed: {
            validClass(){
				return this.pattern.test(this.value) ? 
						'fa-check-circle text-success' :
						'fa-exclamation-circle text-danger';
			}
        },
        methods: {
            sendVal(e) {
                this.activated = true;

                this.$emit('input-triger', {
                    value: e.target.value, 
                    index: this.index,
                    valid: this.pattern.test(e.target.value)
                });
                
            },
        }
    }
</script>

