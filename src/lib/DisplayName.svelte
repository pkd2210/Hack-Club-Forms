<script>
    import { onMount } from "svelte";

    let { slackId, value = $bindable(''), name = 'displayName'  } = $props();
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
                value = displayName;
                throw new Error(`Displayname: error status: ${response.status}`);
            }
            const data = await response.json();
            displayName = data.displayName || 'Unknown';
            value = displayName;
        } catch (error) {
            console.error('Display name error:', error);
            displayName = 'Error';
            value = displayName;
        }
    }
</script>
<span>{displayName}</span>