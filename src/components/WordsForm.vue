<template>
  <div class="row" id="wordsForm">
  	<div class="col-md-6 col-md-offset-3">
	    <form id="transForm" class="form-inline well" v-on:submit="formSubmit">
	    	<input class="form-control" type="text" v-model="words" placeholder="Enter a word..." required="required" />
	    	<select class="form-control" v-model="language">
	    		<option value="id">Indonesian</option>
	    		<option value="ru">Russian</option>
	    		<option value="es">Spanish</option>
	    		<option value="ko">Korean</option>
	    		<option value="ja">Japanese</option>
	    		<option value="ar">Arabic</option>
	    		<option value="zh">Chinese</option>
	    		<option value="de">German</option>
	    		<option value="pt">Portuguese</option>
	    		<option value="it">Italian</option>
	    	</select>
	    	<input class="btn btn-primary" type="submit" value="TRANSLATE">
	    </form>
    </div>
  </div>
  
</template>

<script>
export default {
  name: 'wordsForm',
  data(){
  	return {
  		words:'',
  		language:''
  	}
  },
  created(){
  	this.language = 'id';
  },
  methods: {
  	formSubmit(e)
  	{
  		this.$emit('formSubmit', this.words, this.language);
  		e.preventDefault();
  	}
  }
}
</script>

<style>
#transForm {
	border-radius:10px;
	border: 1px solid #ccc;
}
</style>