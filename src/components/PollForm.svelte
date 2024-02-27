<script>
  import Button from "../shared/Button.svelte";

    let fields = {question: '', answerA: '', answerB: ''}
    let errors = {question:'', answerA: '', answerB: ''}
    let valid = false;

    const handleSubmit = (e) => {
        e.preventDefault()
        
        valid=true;

        //validate question
        if(fields.question.trim().length < 5){
            valid=false;
            errors.question = 'Question must be at least 5 characters long'
        } else {
            errors.question = ''
        }

        //validate answerA
        if(fields.answerA.trim().length < 1){
            valid=false;
            errors.answerA = 'Answer A must not be empty'
        } else {
            errors.answerA = ''
        }
        
        //validate answerB
        if(fields.answerB.trim().length < 1){
            valid=false;
            errors.answerB = 'Answer B must not be empty'
        } else {
            errors.answerB = ''
        }

        if(valid){
            alert('Submitted!')
            console.log('Valid', fields)
        }
    }

</script>

<form on:submit = {handleSubmit}>
    <div class='form-field'>
        <label for="question">Poll Question</label>
        <input type="text" id="question" bind:value={fields.question}>
        <div class="error">{errors.question}</div>
    </div>
    <div class='form-field'>
        <label for="answer-a">Answer A</label>
        <input type="text" id="answer-a" bind:value={fields.answerA}>
        <div class="error">{errors.answerA}</div>
    </div>
    <div class='form-field'>
        <label for="answer-b">Answer B</label>
        <input type="text" id="answer-b" bind:value={fields.answerB}>
        <div class="error">{errors.answerB}</div>
    </div>
    <Button flat={true}>Add Poll</Button>
</form>

<style>
    form{
        width: 400px;
        margin: 0 auto;
        text-align: center;
    }
    .form-field{
        margin: 2rem auto;
    }
    label{
        text-align: left;
        margin: 1rem auto;
    }
    input{
        width: 100%;
        border-radius: 6px;
    }
    .error{
        color: red;
    }
</style>