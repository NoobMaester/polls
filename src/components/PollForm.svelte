<script>
    let fields = {question: '', answerA: '', answerB: '',}

    const handleSubmit = (e) => {
        e.preventDefault()
        console.log(fields)
    }
</script>

<form on:submit = {handleSubmit}>
    <div class='form-field'>
        <label for="question">Poll Question</label>
        <input type="text" id="question" bind:value={fields.question}>
    </div>
    <div class='form-field'>
        <label for="answer-a">Answer A</label>
        <input type="text" id="answer-a" bind:value={fields.answerA}>
    </div>
    <div class='form-field'>
        <label for="answer-b">Answer B</label>
        <input type="text" id="answer-b" bind:value={fields.answerB}>
    </div>
    <button>Add Poll</button>
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
</style>