<script>
  import Card from "../shared/Card.svelte";
  export let poll;
</script>

<Card>
  <div class="poll">
    <h3>{poll.question}</h3>
    <div class="answer">
      <div class="percent"></div>
      <span>{poll.answerA} ({poll.votesA})</span>
    </div>
    <div class="answer">
      <div class="percent"></div>
      <span>{poll.answerB} ({poll.votesB})</span>
    </div>
  </div>
</Card>

<style>
  h3 {
    margin: 0 auto;
    color: #555;
  }
  .answer {
    background: rgba(129, 3, 247, 0.306);
    cursor: pointer;
    margin: 1rem auto;
    position: relative;
  }
  .answer:hover {
    opacity: 0.6;
  }
  span {
    display: inline-block;
    padding: 1rem 2rem;
  }
</style>
