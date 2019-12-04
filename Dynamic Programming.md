<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Dynamic Programming</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__html"><hr>
<hr>
<hr>
<hr>
<h1 id="dynamic-programming">Dynamic Programming</h1>
<h2 id="sliding-window-maximum">239. Sliding Window Maximum</h2>
<h2 id="maximum-subarray">53. MaximuSubarray</h2>
<ul>
<li>Two Cases:</li>
</ul>
<ol>
<li>If the maxi the previous point  0 (stored in <code>curr_</code>`) : then the maximum: of the cent point is restarted</li>
</ol>
<pre class="  language-python"><code class="prism  language-python"><span class="token keyword">if</span> curr_max <span class="token operator">&lt;</span> <span class="token number">0</span><span class="token punctuation">:</span>
	curr_max <span class="token operator">=</span> nums<span class="token punctuation">[</span>i<span class="token punctuation">]</span>
</code></pre>
<ol start="2">
<li>If the maximum of the previous point <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mo>≥</mo><mo>≥</mo><mo>≥</mo><mo>≥</mo><mo>≥</mo><mo>≥</mo><mo>≥</mo><mo>≥</mo><mo>≥</mo></mrow><annotation encoding="application/x-tex">≥≥≥≥\geq≥≥≥≥</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.77194em; vertical-align: -0.13597em;"></span><span class="mrel">≥</span></span><span class="base"><span class="strut" style="height: 0.77194em; vertical-align: -0.13597em;"></span><span class="mrel">≥</span></span><span class="base"><span class="strut" style="height: 0.77194em; vertical-align: -0.13597em;"></span><span class="mrel">≥</span></span><span class="base"><span class="strut" style="height: 0.77194em; vertical-align: -0.13597em;"></span><span class="mrel">≥</span></span><span class="base"><span class="strut" style="height: 0.77194em; vertical-align: -0.13597em;"></span><span class="mrel">≥</span></span><span class="base"><span class="strut" style="height: 0.77194em; vertical-align: -0.13597em;"></span><span class="mrel">≥</span></span><span class="base"><span class="strut" style="height: 0.77194em; vertical-align: -0.13597em;"></span><span class="mrel">≥</span></span><span class="base"><span class="strut" style="height: 0.77194em; vertical-align: -0.13597em;"></span><span class="mrel">≥</span></span><span class="base"><span class="strut" style="height: 0.77194em; vertical-align: -0.13597em;"></span><span class="mrel">≥</span></span></span></span></span> 0: the maximum of the current point is culmulated</li>
</ol>
<pre class="  language-python"><code class="prism  language-python"><span class="token keyword">else</span><span class="token punctuation">:</span>
	curr_max <span class="token operator">+=</span> nums<span class="token punctuation">[</span>i<span class="token punctuation">]</span>
</code></pre>
<ul>
<li>DP Storage: Update the <code>`nums[i]</code><br>
<code>nums[i]</code>`
`nums[i]` store the global maximum so far: compare the <code>`curr_max</code> to <code>nums[i-1]</code></li>
</ul>
<pre class="  language-python"><code class="prism  language-python">nums<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">=</span> <span class="token builtin">max</span><span class="token punctuation">(</span>curr_max<span class="token punctuation">,</span> nums<span class="token punctuation">[</span>i<span class="token number">-1</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
</code></pre>` to `nums[i-1]`
```python
nums[i] = max(curr_max, nums[i-1])
```
</div>
</body>

</html>
<!--stackedit_data:
eyJoaXN0b3J5IjpbODYyOTcxNzY0XX0=
-->