<script>
    import Avatar from '$lib/Avatar.svelte';
    import AvatarUrl from '$lib/AvatarUrl.svelte';
    import DisplayName from '$lib/DisplayName.svelte';
    import Pronouns from '$lib/Pronouns.svelte';
</script>
<h1>Welcome to Hackclub Forms!</h1>
<p>Examples:</p>
<p>For slackId = U091DE0M4NB</p>
<DisplayName slackId="U091DE0M4NB" />
<Pronouns slackId="U091DE0M4NB" />
<Avatar slackId="U091DE0M4NB" />
<AvatarUrl slackId="U091DE0M4NB" />