<script>
    import { onMount } from "svelte";

    let { slackId, startingDate, value = $bindable(''), name = 'hackatimeProjects' } = $props();
    const url = $derived(`https://hackatime.hackclub.com/api/v1/users/${slackId}/stats?features=projects&start_date=${startingDate}`);

    let projects = $state([]);

    onMount(() => {
        fetchProjects();
    });

    async function fetchProjects() {
        try {
            const response = await fetch(url);
            if (!response.ok) {
                projects = [];
                throw new Error(`Hackatime Projects: error status: ${response.status}`);
            }

            const data = await response.json();
            const projectList = data?.data?.projects || data?.projects || [];
            projects = Array.isArray(projectList) ? projectList : [];
        } catch (error) {
            console.error('Hackatime Projects error:', error);
            projects = [];
        }
    }
</script>
<select name={name} bind:value>
{#each projects as project}
    <option value={project.name}>{project.name} - {project.text}</option>
{/each}
</select>