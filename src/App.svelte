<script>
  import Footer from "./components/Footer.svelte";
  import Header from "./components/Header.svelte";
  import PollForm from "./components/PollForm.svelte";
  import Tabs from "./shared/Tabs.svelte";
  import PollList from "./components/PollList.svelte";

  //tabs
  let items = ["Current Polls", "Add New Poll"];
  let activeItem = "Current Polls";
  const tabChange = (e) => {
    activeItem = e.detail;
  };

  //polls
  let polls = [
    {
      id: 1,
      question: "Python or JavaScript",
      answerA: "Python",
      answerB: "JavaScript",
      votesA: 9,
      votesB: 15,
    },
  ];

  const handleAdd = (e) => {
    const poll = e.detail;
    polls = [poll, ...polls];
    console.log(polls);
    activeItem = "Current Polls";
  };

  const handleVote = (e) => {
    const {option, id} = e.detail;

    let copied = [...polls]
    let upvoted = copied.find((poll) => poll.id = id);

    if(option === 'a'){
      upvoted.votesA++;
    }
    if(option === 'b'){
      upvoted.votesB++;
    }
    
    polls = copied;
  }
</script>

<Header />
<main>
  <Tabs {activeItem} {items} on:tabChange={tabChange} />
  {#if activeItem === "Current Polls"}
    <PollList {polls} on:vote={handleVote} />
  {:else if activeItem === "Add New Poll"}
    <PollForm on:add={handleAdd} />
  {/if}
</main>
<Footer />

<style>
  main {
    max-width: 960px;
    margin: 2rem auto;
  }
</style>
