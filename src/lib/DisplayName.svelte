<script>
    import { onMount } from "svelte";

    const { slackId } = $props();
    const url = $derived(`https://cachet.dunkirk.sh/users/${slackId}`);

    let displayName = $state('Loading...');
    onMount(() => {
        fetchDisplayName();
    });
    async function fetchDisplayName() {
        try {
            const response = await fetch(url);
            if (!response.ok) {
                displayName = 'Error';
                throw new Error(`Displayname: error status: ${response.status}`);
            }
            const data = await response.json();
            displayName = data.displayName || 'Unknown';
        } catch (error) {
            console.error('Display name error:', error);
            displayName = 'Error';
        }
    }
</script>
<span>{displayName}</span>