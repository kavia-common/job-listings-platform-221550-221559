<script lang="ts">
    import JobList from '../lib/components/JobList.svelte';
    import JobDetails from '../lib/components/JobDetails.svelte';
    import ApplyForm from '../lib/components/ApplyForm.svelte';
    import HeaderControls from '../lib/components/HeaderControls.svelte';
    import { getJobs, type Job } from '../lib/data/jobs';
    import { selectedJobId } from '../lib/stores';

    let showDetails = $state(false);
    let showApply = $state(false);

    let jobs: Job[] = $state([]);

    // Only fetch on client to avoid SSR fetch/env access differences
    if (typeof window !== 'undefined') {
        $effect(() => {
            getJobs().then((data) => (jobs = data));
        });
    }

    function openDetails(id: string) {
        selectedJobId.set(id);
        showDetails = true;
    }

    function closeModals() {
        showDetails = false;
        showApply = false;
        selectedJobId.set(null);
    }
</script>

<svelte:head>
    <title>Ocean Jobs — Find your next role</title>
</svelte:head>

<section class="card" style="padding: 1rem; margin-bottom: 1rem;">
    <HeaderControls />
</section>

<section aria-label="Job Listings">
    <JobList {jobs} onopenDetails={(e) => openDetails(e.detail)} />
</section>

{#if showDetails}
    <JobDetails on:close={closeModals} on:apply={() => { showDetails = false; showApply = true; }} />
{/if}

{#if showApply}
    <ApplyForm on:close={closeModals} />
{/if}
