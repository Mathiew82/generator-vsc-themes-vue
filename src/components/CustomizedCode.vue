<template>
  <pre>
<span class="symbols">&lt;</span><span class="tags">template</span><span class="symbols">&gt;</span>
  <span class="symbols">&lt;</span><span class="tags">input</span>
    <span class="keywords">v-model</span><span class="symbols">="</span><span class="variables">model</span><span class="symbols">"</span>
    <span class="keywords">class</span><span class="symbols">="</span><span class="strings">ui-input py-2 px-5 rounded-full text-sm text-white outline-0</span><span class="symbols">"</span>
    <span class="symbols">:</span><span class="keywords">class</span><span class="symbols">="</span><span class="variables">defaultStyles</span><span class="symbols">"</span>
  <span class="symbols">/&gt;</span>
<span class="symbols">&lt;/</span><span class="tags">template</span><span class="symbols">&gt;</span>

<span class="symbols">&lt;</span><span class="tags">script</span> <span class="keywords">setup lang</span><span class="symbols">="</span><span class="strings">ts</span><span class="symbols">"</span><span class="symbols">&gt;</span>
<span class="directives">import</span> <span class="keys">{</span> <span class="tags">ref</span> <span class="keys">}</span> <span class="directives">from</span> <span class="symbols">'</span><span class="strings">vue</span><span class="symbols">'</span>
<span class="directives">import</span> <span class="keys">{</span> <span class="tags">useType</span> <span class="keys">}</span> <span class="directives">from</span> <span class="symbols">'</span><span class="strings">~/components/ui/composable/useType</span><span class="symbols">'</span>
<span class="directives">import type</span> <span class="keys">{</span> <span class="tags">Event</span> <span class="keys">}</span> <span class="directives">from</span> <span class="symbols">'</span><span class="strings">@/types/Event</span><span class="symbols">'</span>

<span class="keywords">const</span> <span class="variables">model</span> = <span class="functions">defineModel</span><span class="keys">&lt;</span><span class="properties-types">string</span><span class="keys">&gt;</span><span class="keys">()</span>

<span class="keywords">const</span> <span class="keys">{</span> <span class="variables">defaultStyles</span> <span class="keys">}</span> = <span class="functions">useType</span><span class="keys">(</span><span class="symbols">'</span><span class="strings">default</span><span class="symbols">'</span><span class="keys">)</span>

<span class="directives">export</span> <span class="keywords">const</span> <span class="functions">useMyEvents</span> = <span class="keys">()</span> <span class="keywords">=></span> <span class="keys">{</span>
  <span class="keywords">const</span> <span class="functions">addEvent</span> <span class="keywords">=</span> <span class="keys">(</span><span class="values">newEvent</span><span class="keywords">:</span> <span class="tags">Event</span><span class="keys">)</span><span class="keywords">:</span> <span class="properties-types">void</span> <span class="keywords">=></span> <span class="keys">{</span>
    <span class="variables">myEvents</span><span class="symbols">.</span><span class="variables">value</span><span class="symbols">.</span><span class="functions">push</span><span class="keys">(</span><span class="values">newEvent</span><span class="keys">)</span>
  <span class="keys">}</span>

  <span class="keywords">const</span> <span class="functions">removeEvent</span> <span class="keywords">=</span> <span class="keys">(</span><span class="values">eventId</span><span class="keywords">:</span> <span class="properties-types">number</span><span class="keys">)</span><span class="keywords">:</span> <span class="properties-types">void</span> <span class="keywords">=></span> <span class="keys">{</span>
    <span class="variables">myEvents</span><span class="symbols">.</span><span class="variables">value</span> <span class="keywords">=</span> <span class="variables">myEvents</span><span class="symbols">.</span><span class="variables">value</span><span class="symbols">.</span><span class="functions">filter</span><span class="keys">(</span><span class="keys">(</span><span class="values">event</span><span class="keys">)</span> <span class="keywords">=></span> <span class="values">event</span><span class="symbols">.</span><span class="variables">id</span> <span class="keywords">!==</span> <span class="values">eventId</span><span class="keys">)</span>
  <span class="keys">}</span>

  <span class="directives">return</span> <span class="keys">{</span>
    <span class="functions">addEvent</span>,
    <span class="functions">removeEvent</span>,
  <span class="keys">}</span>
<span class="keys">}</span>
<span class="symbols">&lt;/</span><span class="tags">script</span><span class="symbols">&gt;</span>

<span class="symbols">&lt;</span><span class="tags">style</span> <span class="keywords">lang</span><span class="symbols">="</span>scss<span class="symbols">"</span><span class="symbols">&gt;</span>
<span class="directives">@use</span> <span class="symbols">'</span><span class="strings">@/assets/scss/variables</span><span class="symbols">'</span> <span class="directives">as</span> <span class="variables">vars</span><span class="symbols">;</span>

<span class="comments">/* UI Library */</span>
<span class="tags">body</span> <span class="keys">{</span>
  <span class="properties-types">background-color</span><span class="symbols">:</span> <span class="values">back</span><span class="symbols">;</span>
  <span class="properties-types">font-family</span><span class="symbols">:</span> <span class="symbols">"</span><span class="strings">Segoe UI</span><span class="symbols">"</span><span class="symbols">,</span> <span class="values">Tahoma</span><span class="symbols">,</span> <span class="values">Geneva</span><span class="symbols">,</span> <span class="values">Verdana</span><span class="symbols">,</span> <span class="values">sans-serif</span><span class="symbols">;</span>
<span class="keys">}</span>

.<span class="tags">input-styles</span> <span class="keys">{</span>
  <span class="directives">@include</span> <span class="variables">mixins</span><span class="symbols">.</span><span class="functions">ui-control</span><span class="symbols">;</span>
  
  <span class="properties-types">width</span><span class="symbols">:</span> <span class="values">150px</span><span class="symbols">;</span>
  <span class="properties-types">color</span><span class="symbols">:</span> <span class="directives">#bbb</span><span class="symbols">;</span>
<span class="keys">}</span>
<span class="symbols">&lt;/</span><span class="tags">style</span><span class="symbols">&gt;</span>
  </pre>
</template>
