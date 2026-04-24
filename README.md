# Hack-Club-Forms
A SvelteKit Component Pack, Meant for making forms With Built-In Hack Club Features Integration (Such As Hackatime Projects, CDN Uploads, And more....)
## Installation
* ```npm install hackclub-forms```
## Features Implemented
* DisplayName - ```<DisplayName slackId="U091DE0M4NB" bind:value={displayName} />```
* Pronouns - ```<Pronouns slackId="U091DE0M4NB" bind:value={pronouns} />```
* Avatar - ```<Avatar slackId="U091DE0M4NB" />```
* Avatar URL - ```<AvatarUrl slackId="U091DE0M4NB" bind:value={avatarUrl} />```
* Hackatime Projects - ```<HackatimeProjects slackId="U091DE0M4NB" startingDate="2026-01-01" bind:value={hackatimeProjectsValue} />```
## When adding componnents
* Add in readme
* run npm version patch
* commit
* create relese
* add in src/lib/index.js the new componnents