<script>
  import { createEventDispatcher } from 'svelte'
  import Card from "../shared/Card.svelte";
  export let poll;
  
  const dispatch = createEventDispatcher();
  
  //handling votes
  const handleVote = (option, id) => {
    dispatch('vote', {option: option, id:id})
  }

  //reactive values
  $:totalVotes = poll.votesA + poll.votesB;
  $: percentA = Math.floor(100/ totalVotes * poll.votesA)
  $: percentB = Math.floor(100/ totalVotes * poll.votesB)

</script>


<Card>
  <div class="poll">
    <h3>{poll.question}</h3>
    
    
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div class="answer" on:click={() => handleVote('a', poll.id)}>
      <!-- svelte-ignore missing-declaration -->
      <div class="percent percent-a" style="width: {percentA}%"></div>
      <span>{poll.answerA} ({poll.votesA})</span>
    </div>
    
    
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div class="answer" on:click={() => handleVote('b', poll.id)}>
      <!-- svelte-ignore missing-declaration -->
      <div class="percent percent-b" style="width: {percentB}%"></div>
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
  .percent{
    height: 100%;
    position: absolute;
    box-sizing: border-box;
  }
  .percent-a{
    border-left: 4px solid rgba(129, 3, 247, 0.306);
    background: rgba(129, 3, 247, 0.306);
  }
  .percent-b{
    border-left: 4px solid rgba(129, 3, 247, 0.306);;
    background: rgba(69, 196, 150, 0.2);
  }
</style>
