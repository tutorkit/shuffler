<template>
  <div>
	  <h2 class="title">Shuffler</h2>
		<div>
			<div class="field">
				<label class="label">repeat</label>
				<div class="control">
					<input class="input" type="number" v-model.number="repeat_count" placeholder="repeat count"/>
				</div>
			</div>
			<div class="field" style="display: none;">
				skip_first: {{skip_first}}<br/>
				skip_last: {{skip_last}}<br/>
				repeat_count: {{repeat_count}}<br/>
			</div>
			<div class="field">
				<div class="control">
					<a class="button is-primary">
						Submit
					</a>
				</div>
			</div>
			
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
			repeat_count: 5
    }
  }
}
</script>
