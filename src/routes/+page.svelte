<script>
    import Avatar from '$lib/Avatar.svelte';
    import AvatarUrl from '$lib/AvatarUrl.svelte';
    import DisplayName from '$lib/DisplayName.svelte';
    import HackatimeProjects from '$lib/HackatimeProjects.svelte';
    import Pronouns from '$lib/Pronouns.svelte';
</script>
<style>
    code {
        background-color: #f0f0f0;
        padding: 2px 4px;
        border-radius: 4px;
        font-family: monospace;
    }
</style>

<div>
<h1>Welcome to Hackclub Forms!</h1>
<p>Examples:</p>
<p>For slackId = U091DE0M4NB</p>
<code>&lt;DisplayName slackId="U091DE0M4NB" /&gt;:</code> <DisplayName slackId="U091DE0M4NB" /><br>
<code>&lt;Pronouns slackId="U091DE0M4NB" /&gt;:</code> <Pronouns slackId="U091DE0M4NB" /><br>
<code>&lt;Avatar slackId="U091DE0M4NB" /&gt;:</code> <Avatar slackId="U091DE0M4NB" /><br>
<code>&lt;AvatarUrl slackId="U091DE0M4NB" /&gt;:</code> <AvatarUrl slackId="U091DE0M4NB" /><br>
<code>&lt;HackatimeProjects slackId="U091DE0M4NB" startingDate="2026-01-01" /&gt;:</code> <HackatimeProjects slackId="U091DE0M4NB" startingDate="2026-01-01" /><br>
</div>