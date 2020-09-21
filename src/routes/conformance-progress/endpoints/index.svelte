<script>
 import {
   confEndpointsRaw,
   confEndpoints
 } from '../../../store/conformance.js';
 import { onMount } from 'svelte';
 import { releasesURL } from '../../../lib/constants.js';

 const endpointsURL = `${releasesURL}/conformance-endpoints.json`;
 onMount(async() => {
   const endpoints = await fetch(endpointsURL).then(res => res.json())
   console.log({endpoints});
   confEndpointsRaw.set(endpoints);
 })
</script>
<h2>Endpoints</h2>
<ul>
{#each $confEndpoints as { endpoint, promotion_release, tested_release}}
  <li>{endpoint}<b>{promotion_release}</b></li>
{/each}
</ul>

