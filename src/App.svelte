<script>
  import Footer from "./components/Footer.svelte";
  import Header from "./components/Header.svelte";
  import PollForm from "./components/PollForm.svelte";
  import Tabs from "./shared/Tabs.svelte";

  //tabs
  let items = ["Current Polls", "Add New Poll"];
  let activeItem = "Current Polls";
  const tabChange = (e) => {
    activeItem = e.detail;
  };
</script>

<Header />
<main>
  <Tabs {activeItem} {items} on:tabChange={tabChange} />
  {#if activeItem === "Current Polls"}
    <p>poll list component</p>
  {:else if activeItem === "Add New Poll"}
    <PollForm />
  {/if}
</main>
<Footer />

<style>
  main {
    max-width: 960px;
    margin: 2rem auto;
  }
</style>
