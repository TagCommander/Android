
<html>
<body>
<p><img alt="alt tag" src="res/logo.png" /></p>
<h1 id="developers-implementation-guide">Developers' Implementation Guide</h1>
<p><strong>Android</strong></p>
<p>Last update : <em>20/12/2016</em><br />
Release version : <em>4.0.1</em></p>
<p><div id="end_first_page" /></p>

<div class="toc">
<ul>
<li><a href="#developers-implementation-guide">Developers' Implementation Guide</a></li>
<li><a href="#introduction">Introduction</a></li>
<li><a href="#adding-a-module-to-your-project">Adding a module to your project</a><ul>
<li><a href="#jcenter">JCenter</a></li>
<li><a href="#jar-file">Jar file</a></li>
<li><a href="#aar-file">Aar file</a></li>
</ul>
</li>
<li><a href="#demo-applications">Demo Applications</a></li>
<li><a href="#support-and-contacts">Support and contacts</a></li>
</ul>
</div>
<h1 id="introduction">Introduction</h1>
<p>TagCommander for mobile is a collection of small SDKs each designed to serve a dedicated purpose.
The modules are the following :</p>
<p><a href="TCCore/README.md">Core : Used as a base by the other modules.</a></p>
<p><a href="TCSDK/README.md">SDK : Tag management system collecting data throught a server-side approach.</a></p>
<p><a href="TCSegment/README.md">Segment : Get your user segmentation from our servers.</a></p>
<p>For each of those modules, please check their respective documentation for more information.</p>
<h1 id="adding-a-module-to-your-project">Adding a module to your project</h1>
<p>If you want to add a module to your android project, you have several possibilities.</p>
<div class="codehilite"><pre>- Using jcenter to manage the dependency.
- Using directly the jar in your project.
- Using the aar file in yout project.
</pre></div>


<p>All of them will require you to modify a bit your build.gradle.</p>
<h2 id="jcenter">JCenter</h2>
<p>The easiest way is to go with JCenter. It will help you get updates on the module on a regular basis without doing much work.</p>
<p>If it's not present in your project's build.gradle add jcenter() in the repository list for the dependency management. It will look something like that:</p>
<div class="codehilite"><pre><span class="n">allprojects</span> <span class="o">{</span>
    <span class="n">repositories</span> <span class="o">{</span>
        <span class="n">jcenter</span><span class="o">()</span>
        <span class="n">mavenCentral</span><span class="o">()</span>
    <span class="o">}</span>
<span class="o">}</span>
</pre></div>


<p>Then in your application's build.gradle always add the core module:</p>
<div class="codehilite"><pre><span class="n">compile</span> <span class="err">&#39;</span><span class="n">com</span><span class="o">.</span><span class="na">tagcommander</span><span class="o">.</span><span class="na">lib</span><span class="o">:</span><span class="n">Core</span><span class="o">:</span><span class="mf">4.0</span><span class="o">.</span><span class="mi">1</span><span class="err">&#39;</span>
</pre></div>


<p>And in addition to the core module you can add the other modules you need the same way. See each module's documentation for more specific information.</p>
<p>For exemple:</p>
<div class="codehilite"><pre><span class="n">compile</span> <span class="err">&#39;</span><span class="n">com</span><span class="o">.</span><span class="na">tagcommander</span><span class="o">.</span><span class="na">lib</span><span class="o">:</span><span class="n">SDK</span><span class="o">:</span><span class="mf">4.0</span><span class="o">.</span><span class="mi">1</span><span class="err">&#39;</span>
<span class="n">compile</span> <span class="err">&#39;</span><span class="n">com</span><span class="o">.</span><span class="na">tagcommander</span><span class="o">.</span><span class="na">lib</span><span class="o">:</span><span class="n">Segment</span><span class="o">:</span><span class="mf">4.0</span><span class="o">.</span><span class="mi">1</span><span class="err">&#39;</span>
</pre></div>


<h2 id="jar-file">Jar file</h2>
<p>If you'd rather use the jar files directly in your project, you can get them from our github account: https://github.com/TagCommander/Android</p>
<div class="warning"></div>

<blockquote>
<p>You will always need to at least add the Core module to your project.</p>
</blockquote>
<p>After you downloaded the modules you need, add them to your libs folder and either ask gradle to compile with all the jars in your lib directory or directly with the chosen files.</p>
<div class="codehilite"><pre><span class="c1">// All the jars.</span>
<span class="n">compile</span> <span class="nf">fileTree</span><span class="o">(</span><span class="n">dir</span><span class="o">:</span> <span class="err">&#39;</span><span class="n">libs</span><span class="err">&#39;</span><span class="o">,</span> <span class="n">include</span><span class="o">:</span> <span class="err">&#39;</span><span class="o">*.</span><span class="na">jar</span><span class="err">&#39;</span><span class="o">)</span>
<span class="c1">// Specific files</span>
<span class="n">compile</span> <span class="nf">files</span><span class="o">(</span><span class="err">&#39;</span><span class="n">libs</span><span class="o">/</span><span class="n">TCCore4</span><span class="o">.</span><span class="mf">0.1</span><span class="o">.</span><span class="na">jar</span><span class="err">&#39;</span><span class="o">)</span>
<span class="n">compile</span> <span class="nf">files</span><span class="o">(</span><span class="err">&#39;</span><span class="n">libs</span><span class="o">/</span><span class="n">TCSDK4</span><span class="o">.</span><span class="mf">0.1</span><span class="o">.</span><span class="na">jar</span><span class="err">&#39;</span><span class="o">)</span>
<span class="n">compile</span> <span class="nf">files</span><span class="o">(</span><span class="err">&#39;</span><span class="n">libs</span><span class="o">/</span><span class="n">TCSegment4</span><span class="o">.</span><span class="mf">0.1</span><span class="o">.</span><span class="na">jar</span><span class="err">&#39;</span><span class="o">)</span>
</pre></div>


<h2 id="aar-file">Aar file</h2>
<p>If you'd rather use the aar files directly in your project, you can get them from our github account: https://github.com/TagCommander/Android</p>
<div class="warning"></div>

<blockquote>
<p>You will always need to at least add the Core module to your project.</p>
</blockquote>
<p>To be able to compile with the aar files, you will first need to tell gradle how to use them properly. In your project's build.gradle complete your repository list with 'flatDir' list in the following exemple:</p>
<div class="codehilite"><pre><span class="n">allprojects</span> <span class="o">{</span>
    <span class="n">repositories</span> <span class="o">{</span>
        <span class="n">mavenCentral</span><span class="o">()</span>
        <span class="n">jcenter</span><span class="o">()</span>
        <span class="n">flatDir</span> <span class="o">{</span>
            <span class="n">dirs</span> <span class="err">&#39;</span><span class="n">libs</span><span class="err">&#39;</span>
        <span class="o">}</span>
    <span class="o">}</span>
<span class="o">}</span>
</pre></div>


<p>After you downloaded the modules you need, add them to your libs folder and ask gradle to compile with them.</p>
<div class="codehilite"><pre><span class="n">compile</span> <span class="o">(</span><span class="n">name</span><span class="o">:</span><span class="err">&#39;</span><span class="n">TCCore</span><span class="o">-</span><span class="n">release</span><span class="o">-</span><span class="mf">4.0</span><span class="o">.</span><span class="mi">1</span><span class="err">&#39;</span><span class="o">,</span> <span class="n">ext</span><span class="o">:</span><span class="err">&#39;</span><span class="n">aar</span><span class="err">&#39;</span><span class="o">)</span>
<span class="n">compile</span> <span class="o">(</span><span class="n">name</span><span class="o">:</span><span class="err">&#39;</span><span class="n">TCSDK</span><span class="o">-</span><span class="n">release</span><span class="o">-</span><span class="mf">4.0</span><span class="o">.</span><span class="mi">1</span><span class="err">&#39;</span><span class="o">,</span> <span class="n">ext</span><span class="o">:</span><span class="err">&#39;</span><span class="n">aar</span><span class="err">&#39;</span><span class="o">)</span>
<span class="n">compile</span> <span class="o">(</span><span class="n">name</span><span class="o">:</span><span class="err">&#39;</span><span class="n">TCSegment</span><span class="o">-</span><span class="n">release</span><span class="o">-</span><span class="mf">4.0</span><span class="o">.</span><span class="mi">1</span><span class="err">&#39;</span><span class="o">,</span> <span class="n">ext</span><span class="o">:</span><span class="err">&#39;</span><span class="n">aar</span><span class="err">&#39;</span><span class="o">)</span>
</pre></div>


<h1 id="demo-applications">Demo Applications</h1>
<p>You can check the demo showcasing our modules on github:</p>
<p><a href="https://github.com/TagCommander/Tag-Demo/tree/master/Android">Tag Demo</a></p>
<p><a href="https://github.com/TagCommander/Segment-Demo/tree/master/Android">Segment Demo</a></p>
<h1 id="support-and-contacts">Support and contacts</h1>
<p><img alt="alt tag" src="res/logo.png" /></p>
<hr />
<p><strong>Support</strong>
<em>support@tagcommander.com</em></p>
<p>http://www.tagcommander.com</p>
<p>TagCommander | 3/5 rue Saint Georges - 75009 PARIS - France</p>
<hr />
<p>This documentation was generated on 20/12/2016 15:01:13</p>
</body>
</html>