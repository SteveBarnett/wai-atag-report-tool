<script>
  import { onMount } from "svelte";
  import { Link, useLocation } from "svelte-navigator";

  import Header from "../components/Header.svelte";
  import ReportHeader from "../components/report/ReportHeader.svelte";
  import ReportSummary from "../components/report/ReportSummary.svelte";
  import ReportResults from "../components/report/ReportResults.svelte";
  import ReportHTMLDownload from "../components/report/ReportHTMLDownload.svelte";
  import ReportJSONDownload from "../components/report/ReportJSONDownload.svelte";

  import { currentPage } from "../stores/currentPage.js";

  import { honourFragmentIdLinks } from "../utils/honourFragmentIdLinks.js";

  const location = useLocation();

  onMount(() => {
    let fragment;
    currentPage.update(currentPage => "Report");

    honourFragmentIdLinks($location);
  });
</script>

<svelte:head>
  <title>Report | ATAG Report Tool | W3C WAI</title>
</svelte:head>

<Header>Report</Header>

<p>
  <ReportHTMLDownload />
  <ReportJSONDownload />
</p>

<ReportHeader />
<ReportSummary />
<ReportResults />

