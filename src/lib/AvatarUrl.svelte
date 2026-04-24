<script>
    import { onMount } from "svelte";

    let { slackId, value = $bindable(''), class: className = '', style = '' } = $props();
    const url = $derived(`https://cachet.dunkirk.sh/users/${slackId}`);

    let logoUrl = $state('');
    onMount(() => {
        fetchLogo();
    });
    async function fetchLogo() {
        try {
            const response = await fetch(url);
            if (!response.ok) {
                logoUrl = '';
                value = logoUrl;
                throw new Error(`Slack Logo: error status: ${response.status}`);
            }
            const data = await response.json();
            logoUrl = data.imageUrl || '';   
            value = logoUrl;
        } catch (error) {
            console.error('Slack Logo error:', error);
            logoUrl = '';
            value = logoUrl;
        }
    }
</script>
<span class={className} style={style}>
{#if logoUrl}
    {logoUrl}
{:else}
    https://l4-bucket.dunkirk.sh/5DjfoBI58Pfw.webp
{/if}
</span>