<script>
    import { onMount } from "svelte";

    const { slackId } = $props();
    const url = $derived(`https://cachet.dunkirk.sh/users/${slackId}`);

    let pronouns = $state('Loading...');
    onMount(() => {
        fetchPronouns();
    });
    async function fetchPronouns() {
        try {
            const response = await fetch(url);
            if (!response.ok) {
                pronouns = 'Error';
                throw new Error(`Pronouns: error status: ${response.status}`);
            }
            const data = await response.json();
            pronouns = data.pronouns || 'Unknown';
        } catch (error) {
            console.error('Pronouns error:', error);
            pronouns = 'Error';
        }
    }
</script>
<span>{pronouns}</span>