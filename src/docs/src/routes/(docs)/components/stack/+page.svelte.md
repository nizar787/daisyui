---
title: Stack
desc: Stack visually puts elements on top of each other.
published: true
layout: components
---

<script>
  import Component from "$components/Component.svelte"
  import ClassTable from "$components/ClassTable.svelte"
  import BrowserSupport from "$components/BrowserSupport.svelte"
  import { prefix } from '$lib/stores';
  import { replace } from '$lib/actions';
</script>

<ClassTable
data="{[
  { type:'component', class: 'stack', desc: 'Puts the child elements on top of each other' },
]}"
/>

<Component title="3 divs without stack">
<div>
  <div class="grid w-32 h-20 rounded bg-primary text-primary-content place-content-center">1</div> 
  <div class="grid w-32 h-20 rounded bg-accent text-accent-content place-content-center">2</div> 
  <div class="grid w-32 h-20 rounded bg-secondary text-secondary-content place-content-center">3</div>
</div>
<pre slot="html" use:replace={{ to: $prefix }}>{
`<div>
  <div class="grid w-32 h-20 rounded bg-primary text-primary-content place-content-center">1</div> 
  <div class="grid w-32 h-20 rounded bg-accent text-accent-content place-content-center">2</div> 
  <div class="grid w-32 h-20 rounded bg-secondary text-secondary-content place-content-center">3</div>
</div>`
}</pre>
</Component>

<Component title="3 divs with stack">
<div class="stack mb-4">
  <div class="grid w-32 h-20 rounded bg-primary text-primary-content place-content-center">1</div> 
  <div class="grid w-32 h-20 rounded bg-accent text-accent-content place-content-center">2</div> 
  <div class="grid w-32 h-20 rounded bg-secondary text-secondary-content place-content-center">3</div>
</div>
<pre slot="html" use:replace={{ to: $prefix }}>{
`<div class="$$stack">
  <div class="grid w-32 h-20 rounded bg-primary text-primary-content place-content-center">1</div> 
  <div class="grid w-32 h-20 rounded bg-accent text-accent-content place-content-center">2</div> 
  <div class="grid w-32 h-20 rounded bg-secondary text-secondary-content place-content-center">3</div>
</div>`
}</pre>
</Component>

<Component title="stacked images">
<div class="stack mb-4">
  <img src="/images/stock/photo-1559703248-dcaaec9fab78.jpg" alt="Tailwind CSS example 1" class="rounded w-28" />
  <img src="/images/stock/photo-1565098772267-60af42b81ef2.jpg" alt="Tailwind CSS example 2" class="rounded w-28" />
  <img src="/images/stock/photo-1572635148818-ef6fd45eb394.jpg" alt="Tailwind CSS example 3" class="rounded w-28" />
</div>
<pre slot="html" use:replace={{ to: $prefix }}>{
`<div class="$$stack">
  <img src="/images/stock/photo-1559703248-dcaaec9fab78.jpg" class="rounded" />
  <img src="/images/stock/photo-1565098772267-60af42b81ef2.jpg" class="rounded" />
  <img src="/images/stock/photo-1572635148818-ef6fd45eb394.jpg" class="rounded" />
</div>`
}</pre>
</Component>

<Component title="stacked cards">
<div class="stack mb-4">
  <div class="text-center border border-base-content card w-36 bg-base-100">
    <div class="card-body">A</div>
  </div> 
  <div class="text-center border border-base-content card w-36 bg-base-100">
    <div class="card-body">B</div>
  </div> 
  <div class="text-center border border-base-content card w-36 bg-base-100">
    <div class="card-body">C</div>
  </div>
</div>
<pre slot="html" use:replace={{ to: $prefix }}>{
`<div class="$$stack">
  <div class="text-center border border-base-content $$card w-36 bg-base-100">
    <div class="$$card-body">A</div>
  </div> 
  <div class="text-center border border-base-content $$card w-36 bg-base-100">
    <div class="$$card-body">B</div>
  </div> 
  <div class="text-center border border-base-content $$card w-36 bg-base-100">
    <div class="$$card-body">C</div>
  </div>
</div>`
}</pre>
</Component>

<Component title="stacked cards with shadow">
<div class="stack mb-4">
  <div class="text-center shadow-md w-36 card bg-base-200">
    <div class="card-body">A</div>
  </div> 
  <div class="text-center shadow w-36 card bg-base-200">
    <div class="card-body">B</div>
  </div> 
  <div class="text-center shadow-sm w-36 card bg-base-200">
    <div class="card-body">C</div>
  </div>
</div>
<pre slot="html" use:replace={{ to: $prefix }}>{
`<div class="$$stack">
  <div class="text-center shadow-md w-36 $$card bg-base-200">
    <div class="$$card-body">A</div>
  </div> 
  <div class="text-center shadow w-36 $$card bg-base-200">
    <div class="$$card-body">B</div>
  </div> 
  <div class="text-center shadow-sm w-36 $$card bg-base-200">
    <div class="$$card-body">C</div>
  </div>
</div>`
}</pre>
</Component>

<Component title="stacked cards">
<div class="stack mb-4">
  <div class="shadow-md card bg-primary text-primary-content">
    <div class="card-body">
      <h2 class="card-title">Notification 1</h2> 
      <p>You have 3 unread messages. Tap here to see.</p>
    </div>
  </div> 
  <div class="shadow card bg-primary text-primary-content">
    <div class="card-body">
      <h2 class="card-title">Notification 2</h2> 
      <p>You have 3 unread messages. Tap here to see.</p>
    </div>
  </div> 
  <div class="shadow-sm card bg-primary text-primary-content">
    <div class="card-body">
      <h2 class="card-title">Notification 3</h2> 
      <p>You have 3 unread messages. Tap here to see.</p>
    </div>
  </div>
</div>
<pre slot="html" use:replace={{ to: $prefix }}>{
`<div class="$$stack">
  <div class="$$card shadow-md bg-primary text-primary-content">
    <div class="$$card-body">
      <h2 class="$$card-title">Notification 1</h2> 
      <p>You have 3 unread messages. Tap here to see.</p>
    </div>
  </div> 
  <div class="$$card shadow bg-primary text-primary-content">
    <div class="$$card-body">
      <h2 class="$$card-title">Notification 2</h2> 
      <p>You have 3 unread messages. Tap here to see.</p>
    </div>
  </div> 
  <div class="$$card shadow-sm bg-primary text-primary-content">
    <div class="$$card-body">
      <h2 class="$$card-title">Notification 3</h2> 
      <p>You have 3 unread messages. Tap here to see.</p>
    </div>
  </div>
</div>`
}</pre>
</Component>
