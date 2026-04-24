<script>
    import { onMount } from "svelte";

    let { slackId, value = $bindable(''), name = 'pronouns' } = $props();
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
                value = pronouns;
                throw new Error(`Pronouns: error status: ${response.status}`);
            }
            const data = await response.json();
            pronouns = data.pronouns || 'Unknown';
            value = pronouns;
        } catch (error) {
            console.error('Pronouns error:', error);
            pronouns = 'Error';
            value = pronouns;
        }
    }
</script>
<span>{pronouns}</span>