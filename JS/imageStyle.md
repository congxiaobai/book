
<body>
<a name="top"></a>
<!--PageBeginHtml Block Begin-->
<link type="text/css" rel="stylesheet" href="https://files.cnblogs.com/whitewolf/screen.css">
<style type="text/css"> img { max-width: 100%;}</style>
<!--PageBeginHtml Block End-->


<div id="container">
    <div id="wrapper">
        <div id="content">
            
<div id="post_detail">
<div class="post" id="post">
    <a name="top"></a>
    <h2><a>前端JavaScript规范</a></h2>

<div class="entry-content">
<h1 id="javascript规范">JavaScript规范</h1>
<h2 id="目录"><a>目录</a></h2>
<ol>
<li><a href="#types">类型</a></li>
<li><a href="#objects">对象</a></li>
<li><a href="#arrays">数组</a></li>
<li><a href="#strings">字符串</a></li>
<li><a href="#functions">函数</a></li>
<li><a href="#properties">属性</a></li>
<li><a href="#variables">变量</a></li>
<li><a href="#conditionals">条件表达式和等号</a></li>
<li><a href="#blocks">块</a></li>
<li><a href="#comments">注释</a></li>
<li><a href="#whitespace">空白</a></li>
<li><a href="#commas">逗号</a></li>
<li><a href="#semicolons">分号</a></li>
<li><a href="#type-coercion">类型转换</a></li>
<li><a href="#naming-conventions">命名约定</a></li>
<li><a href="#accessors">存取器</a></li>
<li><a href="#constructors">构造器</a></li>
<li><a href="#events">事件</a></li>
<li><a href="#modules">模块</a></li>
<li><a href="#jquery">jQuery</a></li>
<li><a href="#es5">ES5 兼容性</a></li>
<li><a href="#html-css-js">HTML、CSS、JavaScript分离</a></li>
<li><a href="#jshint">使用jsHint</a></li>
<li><a href="#tools">前端工具</a></li>
</ol>
<h2 id="类型"><a>类型</a></h2>
<ul>
<li>
<p><strong>原始值</strong>: 相当于传值(JavaScript对象都提供了字面量)，使用字面量创建对象。</p>
<ul>
<li><code>string</code></li>
<li><code>number</code></li>
<li><code>boolean</code></li>
<li><code>null</code></li>
<li><code>undefined</code></li>
</ul>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-keyword">var</span> foo = <span class="hljs-number">1</span>,
    bar = foo;

bar = <span class="hljs-number">9</span>;

console.log(foo, bar); <span class="hljs-comment">// =&gt; 1, 9</span></code></pre>
</li>
<li>
<p><strong>复杂类型</strong>: 相当于传引用</p>
<ul>
<li><code>object</code></li>
<li><code>array</code></li>
<li><code>function</code></li>
</ul>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-keyword">var</span> foo = [<span class="hljs-number">1</span>, <span class="hljs-number">2</span>],
    bar = foo;

bar[<span class="hljs-number">0</span>] = <span class="hljs-number">9</span>;

console.log(foo[<span class="hljs-number">0</span>], bar[<span class="hljs-number">0</span>]); <span class="hljs-comment">// =&gt; 9, 9</span></code></pre>
</li>
</ul>
<h2 id="对象"><a>对象</a></h2>
<ul>
<li>
<p>使用字面值创建对象</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> item = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Object</span>();

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> item = {};</code></pre>
</li>
<li>
<p>不要使用保留字 <a href="https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Reserved_Words">reserved words</a> 作为键</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> superman = {
  <span class="hljs-keyword">class</span>: <span class="hljs-string">'superhero'</span>,
  <span class="hljs-keyword">default</span>: { clark: <span class="hljs-string">'kent'</span> },
  private: <span class="hljs-literal">true</span>
};

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> superman = {
  klass: <span class="hljs-string">'superhero'</span>,
  defaults: { clark: <span class="hljs-string">'kent'</span> },
  hidden: <span class="hljs-literal">true</span>
};</code></pre>
</li>
</ul>
<h2 id="数组"><a>数组</a></h2>
<ul>
<li>
<p>使用字面值创建数组</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> items = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Array</span>();

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> items = [];</code></pre>
</li>
<li>
<p>如果你不知道数组的长度，使用push</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-keyword">var</span> someStack = [];


<span class="hljs-comment">// bad</span>
someStack[someStack.length] = <span class="hljs-string">'abracadabra'</span>;

<span class="hljs-comment">// good</span>
someStack.push(<span class="hljs-string">'abracadabra'</span>);</code></pre>
</li>
<li>
<p>当你需要拷贝数组时使用slice. <a href="http://jsperf.com/converting-arguments-to-an-array/7">jsPerf</a></p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-keyword">var</span> len = items.length,
    itemsCopy = [],
    i;

<span class="hljs-comment">// bad</span>
<span class="hljs-keyword">for</span> (i = <span class="hljs-number">0</span>; i &lt; len; i++) {
  itemsCopy[i] = items[i];
}

<span class="hljs-comment">// good</span>
itemsCopy = items.slice();</code></pre>
</li>
<li>
<p>使用slice将类数组的对象转成数组.</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">trigger</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">var</span> args = [].slice.apply(<span class="hljs-built_in">arguments</span>);
  ...
}</code></pre>
</li>
</ul>
<h2 id="字符串"><a>字符串</a></h2>
<ul>
<li>
<p>对字符串使用单引号 <code>''</code>(因为大多时候我们的字符串。特别html会出现<code>"</code>)</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> name = <span class="hljs-string">"Bob Parr"</span>;

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> name = <span class="hljs-string">'Bob Parr'</span>;

<span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> fullName = <span class="hljs-string">"Bob "</span> + <span class="hljs-keyword">this</span>.lastName;

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> fullName = <span class="hljs-string">'Bob '</span> + <span class="hljs-keyword">this</span>.lastName;</code></pre>
</li>
<li>
<p>超过80(也有规定140的，项目具体可制定)个字符的字符串应该使用字符串连接换行</p>
</li>
<li>
<p>注: 如果过度使用，长字符串连接可能会对性能有影响. <a href="http://jsperf.com/ya-string-concat">jsPerf</a> &amp; <a href="https://github.com/airbnb/javascript/issues/40">Discussion</a></p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> errorMessage = <span class="hljs-string">'This is a super long error that was thrown because of Batman. When you stop to think about how Batman had anything to do with this, you would get nowhere fast.'</span>;

<span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> errorMessage = <span class="hljs-string">'This is a super long error that \
was thrown because of Batman. \
When you stop to think about \
how Batman had anything to do \
with this, you would get nowhere \
fast.'</span>;


<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> errorMessage = <span class="hljs-string">'This is a super long error that '</span> +
  <span class="hljs-string">'was thrown because of Batman.'</span> +
  <span class="hljs-string">'When you stop to think about '</span> +
  <span class="hljs-string">'how Batman had anything to do '</span> +
  <span class="hljs-string">'with this, you would get nowhere '</span> +
  <span class="hljs-string">'fast.'</span>;</code></pre>
</li>
<li>
<p>编程时使用join而不是字符串连接来构建字符串，特别是IE: <a href="http://jsperf.com/string-vs-array-concat/2">jsPerf</a>.</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-keyword">var</span> items,
    messages,
    length, i;

messages = [{
    state: <span class="hljs-string">'success'</span>,
    message: <span class="hljs-string">'This one worked.'</span>
},{
    state: <span class="hljs-string">'success'</span>,
    message: <span class="hljs-string">'This one worked as well.'</span>
},{
    state: <span class="hljs-string">'error'</span>,
    message: <span class="hljs-string">'This one did not work.'</span>
}];

length = messages.length;

<span class="hljs-comment">// bad</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">inbox</span><span class="hljs-params">(messages)</span> {</span>
  items = <span class="hljs-string">'&lt;ul&gt;'</span>;

  <span class="hljs-keyword">for</span> (i = <span class="hljs-number">0</span>; i &lt; length; i++) {
    items += <span class="hljs-string">'&lt;li&gt;'</span> + messages[i].message + <span class="hljs-string">'&lt;/li&gt;'</span>;
  }

  <span class="hljs-keyword">return</span> items + <span class="hljs-string">'&lt;/ul&gt;'</span>;
}

<span class="hljs-comment">// good</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">inbox</span><span class="hljs-params">(messages)</span> {</span>
  items = [];

  <span class="hljs-keyword">for</span> (i = <span class="hljs-number">0</span>; i &lt; length; i++) {
    items[i] = messages[i].message;
  }

  <span class="hljs-keyword">return</span> <span class="hljs-string">'&lt;ul&gt;&lt;li&gt;'</span> + items.join(<span class="hljs-string">'&lt;/li&gt;&lt;li&gt;'</span>) + <span class="hljs-string">'&lt;/li&gt;&lt;/ul&gt;'</span>;
}</code></pre>
</li>
</ul>
<h2 id="函数"><a>函数</a></h2>
<ul>
<li>
<p>函数表达式:</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// 匿名函数表达式</span>
<span class="hljs-keyword">var</span> anonymous = <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">return</span> <span class="hljs-literal">true</span>;
};

<span class="hljs-comment">// 有名函数表达式</span>
<span class="hljs-keyword">var</span> named = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">named</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">return</span> <span class="hljs-literal">true</span>;
};

<span class="hljs-comment">// 立即调用函数表达式</span>
(<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
  console.log(<span class="hljs-string">'Welcome to the Internet. Please follow me.'</span>);
})();</code></pre>
</li>
<li>
<p>绝对不要在一个非函数块里声明一个函数，把那个函数赋给一个变量。浏览器允许你这么做，但是它们解析不同。</p>
</li>
<li>
<p><strong>注:</strong> ECMA-262定义把<code>块</code>定义为一组语句，函数声明不是一个语句。<a href="http://www.ecma-international.org/publications/files/ECMA-ST/Ecma-262.pdf#page=97">阅读ECMA-262对这个问题的说明</a>.</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">if</span> (currentUser) {
  <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">test</span><span class="hljs-params">()</span> {</span>
    console.log(<span class="hljs-string">'Nope.'</span>);
  }
}

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">if</span> (currentUser) {
  <span class="hljs-keyword">var</span> test = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">test</span><span class="hljs-params">()</span> {</span>
    console.log(<span class="hljs-string">'Yup.'</span>);
  };
}</code></pre>
</li>
<li>
<p>绝对不要把参数命名为 <code>arguments</code>, 这将会逾越函数作用域内传过来的 <code>arguments</code> 对象.</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">nope</span><span class="hljs-params">(name, options, arguments)</span> {</span>
  <span class="hljs-comment">// ...stuff...</span>
}

<span class="hljs-comment">// good</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">yup</span><span class="hljs-params">(name, options, args)</span> {</span>
  <span class="hljs-comment">// ...stuff...</span>
}</code></pre>
</li>
</ul>
<h2 id="属性"><a>属性</a></h2>
<ul>
<li>
<p>当使用变量和特殊非法变量名时，访问属性时可以使用中括号(<code>.</code> 优先).</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-keyword">var</span> luke = {
  jedi: <span class="hljs-literal">true</span>,
  age: <span class="hljs-number">28</span>
};

<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getProp</span><span class="hljs-params">(prop)</span> {</span>
  <span class="hljs-keyword">return</span> luke[prop];
}

<span class="hljs-keyword">var</span> isJedi = getProp(<span class="hljs-string">'jedi'</span>);</code></pre>
</li>
</ul>
<h2 id="变量"><a>变量</a></h2>
<ul>
<li>
<p>总是使用 <code>var</code> 来声明变量，如果不这么做将导致产生全局变量，我们要避免污染全局命名空间。</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
superPower = <span class="hljs-keyword">new</span> SuperPower();

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> superPower = <span class="hljs-keyword">new</span> SuperPower();</code></pre>
</li>
<li>
<p>使用ES6以及以上的版本时，总是使用 <code>let</code> 来声明变量</p>
<pre class="prettyprint"> let 声明变量,可以使用块作用域，防止函数作用域引起的for循环错误</pre>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
superPower = <span class="hljs-keyword">new</span> SuperPower();

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">let</span> superPower = <span class="hljs-keyword">new</span> SuperPower();</code></pre>
</li>
<li>
<p>使用一个 <code>var</code> 以及新行声明多个变量，缩进4个空格。</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> items = getItems();
<span class="hljs-keyword">var</span> goSportsTeam = <span class="hljs-literal">true</span>;
<span class="hljs-keyword">var</span> dragonball = <span class="hljs-string">'z'</span>;

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> items = getItems(),
    goSportsTeam = <span class="hljs-literal">true</span>,
    dragonball = <span class="hljs-string">'z'</span>;</code></pre>
</li>
<li>
<p>最后再声明未赋值的变量，当你想引用之前已赋值变量的时候很有用。</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> i, len, dragonball,
    items = getItems(),
    goSportsTeam = <span class="hljs-literal">true</span>;

<span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> i, items = getItems(),
    dragonball,
    goSportsTeam = <span class="hljs-literal">true</span>,
    len;

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> items = getItems(),
    goSportsTeam = <span class="hljs-literal">true</span>,
    dragonball,
    length,
    i;</code></pre>
</li>
<li>
<p>在作用域顶部声明变量，避免变量声明和赋值引起的相关问题。</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
  test();
  console.log(<span class="hljs-string">'doing stuff..'</span>);

  <span class="hljs-comment">//..other stuff..</span>

  <span class="hljs-keyword">var</span> name = getName();

  <span class="hljs-keyword">if</span> (name === <span class="hljs-string">'test'</span>) {
    <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>;
  }

  <span class="hljs-keyword">return</span> name;
}

<span class="hljs-comment">// good</span>
<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">var</span> name = getName();

  test();
  console.log(<span class="hljs-string">'doing stuff..'</span>);

  <span class="hljs-comment">//..other stuff..</span>

  <span class="hljs-keyword">if</span> (name === <span class="hljs-string">'test'</span>) {
    <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>;
  }

  <span class="hljs-keyword">return</span> name;
}

<span class="hljs-comment">// bad</span>
<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">var</span> name = getName();

  <span class="hljs-keyword">if</span> (!<span class="hljs-built_in">arguments</span>.length) {
    <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>;
  }

  <span class="hljs-keyword">return</span> <span class="hljs-literal">true</span>;
}

<span class="hljs-comment">// good</span>
<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">if</span> (!<span class="hljs-built_in">arguments</span>.length) {
    <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>;
  }

  <span class="hljs-keyword">var</span> name = getName();

  <span class="hljs-keyword">return</span> <span class="hljs-literal">true</span>;
}</code></pre>
</li>
</ul>
<h2 id="条件表达式和等号"><a>条件表达式和等号</a></h2>
<ul>
<li>合理使用 <code>===</code> 和 <code>!==</code> 以及 <code>==</code> 和 <code>!=</code>.</li>
<li>合理使用表达式逻辑操作运算.</li>
<li>
<p>条件表达式的强制类型转换遵循以下规则：</p>
<ul>
<li><strong>对象</strong> 被计算为 <strong>true</strong></li>
<li><strong>Undefined</strong> 被计算为 <strong>false</strong></li>
<li><strong>Null</strong> 被计算为 <strong>false</strong></li>
<li><strong>布尔值</strong> 被计算为 <strong>布尔的值</strong></li>
<li><strong>数字</strong> 如果是 <strong>+0, -0, or NaN</strong> 被计算为 <strong>false</strong> , 否则为 <strong>true</strong></li>
<li><strong>字符串</strong> 如果是空字符串 <code>''</code> 则被计算为 <strong>false</strong>, 否则为 <strong>true</strong></li>
</ul>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-keyword">if</span> ([<span class="hljs-number">0</span>]) {
  <span class="hljs-comment">// true</span>
  <span class="hljs-comment">// An array is an object, objects evaluate to true</span>
}</code></pre>
</li>
<li>
<p>使用快捷方式.</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">if</span> (name !== <span class="hljs-string">''</span>) {
  <span class="hljs-comment">// ...stuff...</span>
}

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">if</span> (name) {
  <span class="hljs-comment">// ...stuff...</span>
}

<span class="hljs-comment">// bad</span>
<span class="hljs-keyword">if</span> (collection.length &gt; <span class="hljs-number">0</span>) {
  <span class="hljs-comment">// ...stuff...</span>
}

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">if</span> (collection.length) {
  <span class="hljs-comment">// ...stuff...</span>
}</code></pre>
</li>
<li>
<p>阅读 <a href="http://javascriptweblog.wordpress.com/2011/02/07/truth-equality-and-javascript/#more-2108">Truth Equality and JavaScript</a> 了解更多</p>
</li>
</ul>
<h2 id="块"><a>块</a></h2>
<ul>
<li>
<p>给所有多行的块使用大括号</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">if</span> (test)
  <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>;

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">if</span> (test) <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>;

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">if</span> (test) {
  <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>;
}

<span class="hljs-comment">// bad</span>
<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span> <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>; }

<span class="hljs-comment">// good</span>
<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>;
}</code></pre>
</li>
</ul>
<h2 id="注释"><a>注释</a></h2>
<ul>
<li>
<p>使用 <code>/** ... */</code> 进行多行注释，包括描述，指定类型以及参数值和返回值</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-comment">// make() returns a new element</span>
<span class="hljs-comment">// based on the passed in tag name</span>
<span class="hljs-comment">//</span>
<span class="hljs-comment">// @param &lt;String&gt; tag</span>
<span class="hljs-comment">// @return &lt;Element&gt; element</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">make</span><span class="hljs-params">(tag)</span> {</span>

  <span class="hljs-comment">// ...stuff...</span>

  <span class="hljs-keyword">return</span> element;
}

<span class="hljs-comment">// good</span>
<span class="hljs-comment">/**
 * make() returns a new element
 * based on the passed in tag name
 *
 * @param &lt;String&gt; tag
 * @return &lt;Element&gt; element
 */</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">make</span><span class="hljs-params">(tag)</span> {</span>

  <span class="hljs-comment">// ...stuff...</span>

  <span class="hljs-keyword">return</span> element;
}</code></pre>
</li>
<li>
<p>使用 <code>//</code> 进行单行注释，在评论对象的上面进行单行注释，注释前放一个空行.</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> active = <span class="hljs-literal">true</span>;  <span class="hljs-comment">// is current tab</span>

<span class="hljs-comment">// good</span>
<span class="hljs-comment">// is current tab</span>
<span class="hljs-keyword">var</span> active = <span class="hljs-literal">true</span>;

<span class="hljs-comment">// bad</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getType</span><span class="hljs-params">()</span> {</span>
  console.log(<span class="hljs-string">'fetching type...'</span>);
  <span class="hljs-comment">// set the default type to 'no type'</span>
  <span class="hljs-keyword">var</span> type = <span class="hljs-keyword">this</span>._type || <span class="hljs-string">'no type'</span>;

  <span class="hljs-keyword">return</span> type;
}

<span class="hljs-comment">// good</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getType</span><span class="hljs-params">()</span> {</span>
  console.log(<span class="hljs-string">'fetching type...'</span>);

  <span class="hljs-comment">// set the default type to 'no type'</span>
  <span class="hljs-keyword">var</span> type = <span class="hljs-keyword">this</span>._type || <span class="hljs-string">'no type'</span>;

  <span class="hljs-keyword">return</span> type;
}</code></pre>
</li>
<li>
<p>如果你有一个问题需要重新来看一下或如果你建议一个需要被实现的解决方法的话需要在你的注释前面加上 <code>FIXME</code> 或 <code>TODO</code> 帮助其他人迅速理解</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">Calculator</span><span class="hljs-params">()</span> {</span>

  <span class="hljs-comment">// FIXME: shouldn't use a global here</span>
  total = <span class="hljs-number">0</span>;

  <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>;
}</code></pre>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">Calculator</span><span class="hljs-params">()</span> {</span>

  <span class="hljs-comment">// TODO: total should be configurable by an options param</span>
  <span class="hljs-keyword">this</span>.total = <span class="hljs-number">0</span>;

  <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>;
}</code></pre>
</li>
<li>满足规范的文档，在需要文档的时候，可以尝试<a href="http://usejsdoc.org/">jsdoc</a>.</li>
</ul>
<h2 id="空白"><a>空白</a></h2>
<ul>
<li>缩进、格式化能帮助团队更快得定位修复代码BUG.</li>
<li>
<p>将tab设为4个空格</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
∙∙<span class="hljs-keyword">var</span> name;
}

<span class="hljs-comment">// bad</span>
<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
∙<span class="hljs-keyword">var</span> name;
}

<span class="hljs-comment">// good</span>
<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
∙∙∙∙<span class="hljs-keyword">var</span> name;
}</code></pre>
</li>
<li>
<p>大括号前放一个空格</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">test</span><span class="hljs-params">()</span>{</span>
  console.log(<span class="hljs-string">'test'</span>);
}

<span class="hljs-comment">// good</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">test</span><span class="hljs-params">()</span> {</span>
  console.log(<span class="hljs-string">'test'</span>);
}

<span class="hljs-comment">// bad</span>
dog.set(<span class="hljs-string">'attr'</span>,{
  age: <span class="hljs-string">'1 year'</span>,
  breed: <span class="hljs-string">'Bernese Mountain Dog'</span>
});

<span class="hljs-comment">// good</span>
dog.set(<span class="hljs-string">'attr'</span>, {
  age: <span class="hljs-string">'1 year'</span>,
  breed: <span class="hljs-string">'Bernese Mountain Dog'</span>
});</code></pre>
</li>
<li>
<p>在做长方法链时使用缩进.</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
$(<span class="hljs-string">'#items'</span>).find(<span class="hljs-string">'.selected'</span>).highlight().end().find(<span class="hljs-string">'.open'</span>).updateCount();

<span class="hljs-comment">// good</span>
$(<span class="hljs-string">'#items'</span>)
  .find(<span class="hljs-string">'.selected'</span>)
    .highlight()
    .end()
  .find(<span class="hljs-string">'.open'</span>)
    .updateCount();

<span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> leds = stage.selectAll(<span class="hljs-string">'.led'</span>).data(data).enter().append(<span class="hljs-string">'svg:svg'</span>).class(<span class="hljs-string">'led'</span>, <span class="hljs-literal">true</span>)
    .attr(<span class="hljs-string">'width'</span>,  (radius + margin) * <span class="hljs-number">2</span>).append(<span class="hljs-string">'svg:g'</span>)
    .attr(<span class="hljs-string">'transform'</span>, <span class="hljs-string">'translate('</span> + (radius + margin) + <span class="hljs-string">','</span> + (radius + margin) + <span class="hljs-string">')'</span>)
    .call(tron.led);

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> leds = stage.selectAll(<span class="hljs-string">'.led'</span>)
    .data(data)
  .enter().append(<span class="hljs-string">'svg:svg'</span>)
    .class(<span class="hljs-string">'led'</span>, <span class="hljs-literal">true</span>)
    .attr(<span class="hljs-string">'width'</span>,  (radius + margin) * <span class="hljs-number">2</span>)
  .append(<span class="hljs-string">'svg:g'</span>)
    .attr(<span class="hljs-string">'transform'</span>, <span class="hljs-string">'translate('</span> + (radius + margin) + <span class="hljs-string">','</span> + (radius + margin) + <span class="hljs-string">')'</span>)
    .call(tron.led);</code></pre>
</li>
</ul>
<h2 id="逗号"><a>逗号</a></h2>
<ul>
<li>
<p>不要将逗号放前面</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> once
  , upon
  , aTime;

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> once,
    upon,
    aTime;

<span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> hero = {
    firstName: <span class="hljs-string">'Bob'</span>
  , lastName: <span class="hljs-string">'Parr'</span>
  , heroName: <span class="hljs-string">'Mr. Incredible'</span>
  , superPower: <span class="hljs-string">'strength'</span>
};

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> hero = {
  firstName: <span class="hljs-string">'Bob'</span>,
  lastName: <span class="hljs-string">'Parr'</span>,
  heroName: <span class="hljs-string">'Mr. Incredible'</span>,
  superPower: <span class="hljs-string">'strength'</span>
};</code></pre>
</li>
<li>
<p>不要加多余的逗号，这可能会在IE下引起错误，同时如果多一个逗号某些ES3的实现会计算多数组的长度。</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> hero = {
  firstName: <span class="hljs-string">'Kevin'</span>,
  lastName: <span class="hljs-string">'Flynn'</span>,
};

<span class="hljs-keyword">var</span> heroes = [
  <span class="hljs-string">'Batman'</span>,
  <span class="hljs-string">'Superman'</span>,
];

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> hero = {
  firstName: <span class="hljs-string">'Kevin'</span>,
  lastName: <span class="hljs-string">'Flynn'</span>
};

<span class="hljs-keyword">var</span> heroes = [
  <span class="hljs-string">'Batman'</span>,
  <span class="hljs-string">'Superman'</span>
];</code></pre>
</li>
</ul>
<h2 id="分号"><a>分号</a></h2>
<ul>
<li>
<p>语句结束一定要加分号</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
(<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">var</span> name = <span class="hljs-string">'Skywalker'</span>
  <span class="hljs-keyword">return</span> name
})()

<span class="hljs-comment">// good</span>
(<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">var</span> name = <span class="hljs-string">'Skywalker'</span>;
  <span class="hljs-keyword">return</span> name;
})();

<span class="hljs-comment">// good</span>
;(<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">var</span> name = <span class="hljs-string">'Skywalker'</span>;
  <span class="hljs-keyword">return</span> name;
})();</code></pre>
</li>
</ul>
<h2 id="类型转换"><a>类型转换</a></h2>
<ul>
<li>在语句的开始执行类型转换.</li>
<li>
<p>字符串:</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">//  =&gt; this.reviewScore = 9;</span>

<span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> totalScore = <span class="hljs-keyword">this</span>.reviewScore + <span class="hljs-string">''</span>;

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> totalScore = <span class="hljs-string">''</span> + <span class="hljs-keyword">this</span>.reviewScore;

<span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> totalScore = <span class="hljs-string">''</span> + <span class="hljs-keyword">this</span>.reviewScore + <span class="hljs-string">' total score'</span>;

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> totalScore = <span class="hljs-keyword">this</span>.reviewScore + <span class="hljs-string">' total score'</span>;</code></pre>
</li>
<li>
<p>对数字使用 <code>parseInt</code> 并且总是带上类型转换的基数.，如<code>parseInt(value, 10)</code></p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-keyword">var</span> inputValue = <span class="hljs-string">'4'</span>;

<span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> val = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Number</span>(inputValue);

<span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> val = +inputValue;

<span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> val = inputValue &gt;&gt; <span class="hljs-number">0</span>;

<span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> val = <span class="hljs-built_in">parseInt</span>(inputValue);

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> val = <span class="hljs-built_in">Number</span>(inputValue);

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> val = <span class="hljs-built_in">parseInt</span>(inputValue, <span class="hljs-number">10</span>);

<span class="hljs-comment">// good</span>
<span class="hljs-comment">/**
 * parseInt was the reason my code was slow.
 * Bitshifting the String to coerce it to a
 * Number made it a lot faster.
 */</span>
<span class="hljs-keyword">var</span> val = inputValue &gt;&gt; <span class="hljs-number">0</span>;</code></pre>
</li>
<li>
<p>布尔值:</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-keyword">var</span> age = <span class="hljs-number">0</span>;

<span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> hasAge = <span class="hljs-keyword">new</span> <span class="hljs-built_in">Boolean</span>(age);

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> hasAge = <span class="hljs-built_in">Boolean</span>(age);

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> hasAge = !!age;</code></pre>
</li>
</ul>
<h2 id="命名约定"><a>命名约定</a></h2>
<ul>
<li>
<p>避免单个字符名，让你的变量名有描述意义。</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">q</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-comment">// ...stuff...</span>
}

<span class="hljs-comment">// good</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">query</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-comment">// ..stuff..</span>
}</code></pre>
</li>
<li>
<p>当命名对象、函数和实例时使用驼峰命名规则</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> OBJEcttsssss = {};
<span class="hljs-keyword">var</span> this_is_my_object = {};
<span class="hljs-keyword">var</span> <span class="hljs-keyword">this</span>-is-my-object = {};
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">c</span><span class="hljs-params">()</span> {</span>};
<span class="hljs-keyword">var</span> u = <span class="hljs-keyword">new</span> user({
  name: <span class="hljs-string">'Bob Parr'</span>
});

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> thisIsMyObject = {};
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">thisIsMyFunction</span><span class="hljs-params">()</span> {</span>};
<span class="hljs-keyword">var</span> user = <span class="hljs-keyword">new</span> User({
  name: <span class="hljs-string">'Bob Parr'</span>
});</code></pre>
</li>
<li>
<p>当命名构造函数或类时使用驼峰式大写</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">user</span><span class="hljs-params">(options)</span> {</span>
  <span class="hljs-keyword">this</span>.name = options.name;
}

<span class="hljs-keyword">var</span> bad = <span class="hljs-keyword">new</span> user({
  name: <span class="hljs-string">'nope'</span>
});

<span class="hljs-comment">// good</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">User</span><span class="hljs-params">(options)</span> {</span>
  <span class="hljs-keyword">this</span>.name = options.name;
}

<span class="hljs-keyword">var</span> good = <span class="hljs-keyword">new</span> User({
  name: <span class="hljs-string">'yup'</span>
});</code></pre>
</li>
<li>
<p>命名私有属性时前面加个下划线 <code>_</code></p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">this</span>.__firstName__ = <span class="hljs-string">'Panda'</span>;
<span class="hljs-keyword">this</span>.firstName_ = <span class="hljs-string">'Panda'</span>;

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">this</span>._firstName = <span class="hljs-string">'Panda'</span>;</code></pre>
</li>
<li>
<p>当保存对 <code>this</code> 的引用时使用 <code>self(python 风格)</code>,避免<code>this issue</code>.Angular建议使用<code>vm(MVVM模式中view-model)</code></p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// good</span>
<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">var</span> self = <span class="hljs-keyword">this</span>;
  <span class="hljs-keyword">return</span> <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
    console.log(self);
  };
}</code></pre>
</li>
</ul>
<h2 id="存取器"><a>存取器</a></h2>
<ul>
<li>属性的存取器函数不是必需的</li>
<li>
<p>如果你确实有存取器函数的话使用getVal() 和 setVal(‘hello’),<code>java getter、setter风格</code>或者<code>jQuery风格</code></p>
</li>
<li>
<p>如果属性是布尔值，使用isVal() 或 hasVal()</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">if</span> (!dragon.age()) {
  <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>;
}

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">if</span> (!dragon.hasAge()) {
  <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>;
}</code></pre>
</li>
<li>
<p>可以创建get()和set()函数，但是要保持一致</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">Jedi</span><span class="hljs-params">(options)</span> {</span>
  options || (options = {});
  <span class="hljs-keyword">var</span> lightsaber = options.lightsaber || <span class="hljs-string">'blue'</span>;
  <span class="hljs-keyword">this</span>.set(<span class="hljs-string">'lightsaber'</span>, lightsaber);
}

Jedi.prototype.set = <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">(key, val)</span> {</span>
  <span class="hljs-keyword">this</span>[key] = val;
};

Jedi.prototype.get = <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">(key)</span> {</span>
  <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>[key];
};</code></pre>
</li>
</ul>
<h2 id="构造器"><a>构造器</a></h2>
<ul>
<li>
<p>给对象原型分配方法，而不是用一个新的对象覆盖原型，覆盖原型会使继承出现问题。</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">Jedi</span><span class="hljs-params">()</span> {</span>
  console.log(<span class="hljs-string">'new jedi'</span>);
}

<span class="hljs-comment">// bad</span>
Jedi.prototype = {
  fight: <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">fight</span><span class="hljs-params">()</span> {</span>
    console.log(<span class="hljs-string">'fighting'</span>);
  },

  block: <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">block</span><span class="hljs-params">()</span> {</span>
    console.log(<span class="hljs-string">'blocking'</span>);
  }
};

<span class="hljs-comment">// good</span>
Jedi.prototype.fight = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">fight</span><span class="hljs-params">()</span> {</span>
  console.log(<span class="hljs-string">'fighting'</span>);
};

Jedi.prototype.block = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">block</span><span class="hljs-params">()</span> {</span>
  console.log(<span class="hljs-string">'blocking'</span>);
};</code></pre>
</li>
<li>
<p>方法可以返回 <code>this</code> 帮助方法可链。</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
Jedi.prototype.jump = <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">this</span>.jumping = <span class="hljs-literal">true</span>;
  <span class="hljs-keyword">return</span> <span class="hljs-literal">true</span>;
};

Jedi.prototype.setHeight = <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">(height)</span> {</span>
  <span class="hljs-keyword">this</span>.height = height;
};

<span class="hljs-keyword">var</span> luke = <span class="hljs-keyword">new</span> Jedi();
luke.jump(); <span class="hljs-comment">// =&gt; true</span>
luke.setHeight(<span class="hljs-number">20</span>) <span class="hljs-comment">// =&gt; undefined</span>

<span class="hljs-comment">// good</span>
Jedi.prototype.jump = <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">this</span>.jumping = <span class="hljs-literal">true</span>;
  <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>;
};

Jedi.prototype.setHeight = <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">(height)</span> {</span>
  <span class="hljs-keyword">this</span>.height = height;
  <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>;
};

<span class="hljs-keyword">var</span> luke = <span class="hljs-keyword">new</span> Jedi();

luke.jump()
  .setHeight(<span class="hljs-number">20</span>);</code></pre>
</li>
<li>
<p>可以写一个自定义的toString()方法，但是确保它工作正常并且不会有副作用。</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">Jedi</span><span class="hljs-params">(options)</span> {</span>
  options || (options = {});
  <span class="hljs-keyword">this</span>.name = options.name || <span class="hljs-string">'no name'</span>;
}

Jedi.prototype.getName = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">getName</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">return</span> <span class="hljs-keyword">this</span>.name;
};

Jedi.prototype.toString = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">toString</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">return</span> <span class="hljs-string">'Jedi - '</span> + <span class="hljs-keyword">this</span>.getName();
};</code></pre>
</li>
</ul>
<h2 id="事件"><a>事件</a></h2>
<ul>
<li>
<p>当给事件附加数据时，传入一个哈希而不是原始值，这可以让后面的贡献者加入更多数据到事件数据里而不用找出并更新那个事件的事件处理器</p>
<pre class="prettyprint"><code class="language-js hljs "><span class="hljs-comment">// bad</span>
$(<span class="hljs-keyword">this</span>).trigger(<span class="hljs-string">'listingUpdated'</span>, listing.id);

...

$(<span class="hljs-keyword">this</span>).on(<span class="hljs-string">'listingUpdated'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">(e, listingId)</span> {</span>
  <span class="hljs-comment">// do something with listingId</span>
});</code></pre>
<p>更好:</p>
<pre class="prettyprint"><code class="language-js hljs "><span class="hljs-comment">// good</span>
$(<span class="hljs-keyword">this</span>).trigger(<span class="hljs-string">'listingUpdated'</span>, { listingId : listing.id });

...

$(<span class="hljs-keyword">this</span>).on(<span class="hljs-string">'listingUpdated'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">(e, data)</span> {</span>
  <span class="hljs-comment">// do something with data.listingId</span>
});</code></pre>
</li>
</ul>
<h2 id="模块"><a>模块</a></h2>
<ul>
<li>这个文件应该以驼峰命名，并在同名文件夹下，同时导出的时候名字一致</li>
<li>对于公开API库可以考虑加入一个名为noConflict()的方法来设置导出的模块为之前的版本并返回它</li>
<li>
<p>总是在模块顶部声明 <code>'use strict';</code>，引入<code>[JSHint规范](http://jshint.com/)</code></p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// fancyInput/fancyInput.js</span>

（<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">(global)</span> {</span>
<span class="hljs-pi">  'use strict'</span>;

  <span class="hljs-keyword">var</span> previousFancyInput = global.FancyInput;

  <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">FancyInput</span><span class="hljs-params">(options)</span> {</span>
    <span class="hljs-keyword">this</span>.options = options || {};
  }

  FancyInput.noConflict = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">noConflict</span><span class="hljs-params">()</span> {</span>
    global.FancyInput = previousFancyInput;
    <span class="hljs-keyword">return</span> FancyInput;
  };

  global.FancyInput = FancyInput;
})(<span class="hljs-keyword">this</span>);</code></pre>
</li>
</ul>
<h2 id="jquery"><a>jQuery</a></h2>
<ul>
<li>
<p>对于jQuery对象以<code>$</code>开头，以和原生DOM节点区分。</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-keyword">var</span> menu = $(<span class="hljs-string">".menu"</span>);

<span class="hljs-comment">// good</span>
<span class="hljs-keyword">var</span> $menu = $(<span class="hljs-string">".menu"</span>);</code></pre>
</li>
<li>
<p>缓存jQuery查询</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">setSidebar</span><span class="hljs-params">()</span> {</span>
  $(<span class="hljs-string">'.sidebar'</span>).hide();

  <span class="hljs-comment">// ...stuff...</span>

  $(<span class="hljs-string">'.sidebar'</span>).css({
    <span class="hljs-string">'background-color'</span>: <span class="hljs-string">'pink'</span>
  });
}

<span class="hljs-comment">// good</span>
<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">setSidebar</span><span class="hljs-params">()</span> {</span>
  <span class="hljs-keyword">var</span> $sidebar = $(<span class="hljs-string">'.sidebar'</span>);
  $sidebar.hide();

  <span class="hljs-comment">// ...stuff...</span>

  $sidebar.css({
    <span class="hljs-string">'background-color'</span>: <span class="hljs-string">'pink'</span>
  });
}</code></pre>
</li>
<li>
<p>对DOM查询使用级联的 <code>$('.sidebar ul')</code> 或 <code>$('.sidebar ul')</code>，<a href="http://jsperf.com/jquery-find-vs-context-sel/16">jsPerf</a></p>
</li>
<li>
<p>对有作用域的jQuery对象查询使用 <code>find</code></p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
$(<span class="hljs-string">'.sidebar'</span>, <span class="hljs-string">'ul'</span>).hide();

<span class="hljs-comment">// bad</span>
$(<span class="hljs-string">'.sidebar'</span>).find(<span class="hljs-string">'ul'</span>).hide();

<span class="hljs-comment">// good</span>
$(<span class="hljs-string">'.sidebar ul'</span>).hide();

<span class="hljs-comment">// good</span>
$(<span class="hljs-string">'.sidebar &gt; ul'</span>).hide();

<span class="hljs-comment">// good (slower)</span>
$sidebar.find(<span class="hljs-string">'ul'</span>);

<span class="hljs-comment">// good (faster)</span>
$($sidebar[<span class="hljs-number">0</span>]).find(<span class="hljs-string">'ul'</span>);</code></pre>
</li>
<li>
<p>每个页面只使用一次document的ready事件，这样便于调试与行为流跟踪。</p>
<pre class="prettyprint"><code class="language-javascript hljs ">$(<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span>{</span>
   <span class="hljs-comment">//do your page init.  </span>
});</code></pre>
</li>
<li>
<p>事件利用<code>jQuery.on</code>从页面分离到JavaScript文件。</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-comment">// bad</span>
&lt;a id=<span class="hljs-string">"myLink"</span> href=<span class="hljs-string">"#"</span> onclick=<span class="hljs-string">"myEventHandler();"</span>&gt;<span class="xml"><span class="hljs-tag">&lt;/<span class="hljs-title">a</span>&gt;</span>

// good
<span class="hljs-tag">&lt;<span class="hljs-title">a</span> <span class="hljs-attribute">id</span>=<span class="hljs-value">"myLink"</span> <span class="hljs-attribute">href</span>=<span class="hljs-value">"#"</span>&gt;</span><span class="hljs-tag">&lt;/<span class="hljs-title">a</span>&gt;</span>

$("#myLink").on("click", myEventHandler);
</span></code></pre>
</li>
<li>
<p>对于Ajax使用promise方式。</p>
<pre class="prettyprint"><code class="language-javascript hljs ">    <span class="hljs-comment">// bad</span>
    $.ajax({
        ...
        success : <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span>{</span>
        },
        error : <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span>{</span>
        } 
    })

    <span class="hljs-comment">// good</span>
    $.ajax({.
        ..
    }).then( <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">( )</span>{</span>
        <span class="hljs-comment">// success</span>
    }, <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">( )</span>{</span>
        <span class="hljs-comment">// error</span>
    })</code></pre>
</li>
<li>
<p>利用promise的deferred对象解决延迟注册问题。</p>
<pre class="prettyprint"><code class="language-javascript hljs "><span class="hljs-keyword">var</span> dtd = $.Deferred(); <span class="hljs-comment">// 新建一个deferred对象</span>
　　<span class="hljs-keyword">var</span> wait = <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">(dtd)</span>{</span>
　　　　<span class="hljs-keyword">var</span> tasks = <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span>{</span>
　　　　　　alert(<span class="hljs-string">"执行完毕！"</span>);
　　　　　　dtd.resolve(); <span class="hljs-comment">// 改变deferred对象的执行状态</span>
　　　　};
　　　　setTimeout(tasks,<span class="hljs-number">5000</span>);
　　　　<span class="hljs-keyword">return</span> dtd;
　　};</code></pre>
</li>
<li>HTML中Style、以及JavaScript中style移到CSS中class，在HTML、JavaScript中引入class，而不是直接style。</li>
</ul>
<h2 id="ecmascript-5兼容性"><a>ECMAScript 5兼容性</a></h2>
<p>尽量采用ES5方法，特别数组map、filter、forEach方法简化日常开发。在老式IE浏览器中引入<a href="https://github.com/es-shims/es5-shim">ES5-shim</a>。或者也可以考虑引入<a href="http://underscorejs.org/">underscore</a>、<a href="https://lodash.com/">lodash</a> 常用辅助库. <br>
  - 参考<a href="https://twitter.com/kangax/">Kangax</a>的 ES5 <a href="http://kangax.github.com/es5-compat-table/">compatibility table</a> <br>
 - <a href="http://www.cnblogs.com/whitewolf/p/4417873.html">JavaScript工具库之Lodash</a> <br>
 - <a href="http://www.cnblogs.com/whitewolf/p/4357916.html">Babel-现在开始使用 ES6</a></p>
<h2 id="htmlcssjavascript分离"><a>HTML、CSS、JavaScript分离</a></h2>
<ul>
<li>页面DOM结构使用HTML，样式则采用CSS，动态DOM操作JavaScript。不要混用在HTML中</li>
<li>分离在不同类型文件，文件link。</li>
<li>HTML、CSS、JavaScript变量名都需要有业务价值。CSS以中划线分割的全小写命名，JavaScript则首字母小写的驼峰命名。</li>
<li>CSS可引入Bootstrap、Foundation等出名响应式设计框架。以及SASS、LESS工具书写CSS。</li>
<li>对于CSS、JavaScript建议合并为单文件，减少Ajax的连接数。也可以引入AMD(Require.js)加载方式。</li>
<li>对于内部大部分企业管理系统，可以尝试采用前端 MVC框架组织代码。如Angular、React + flux架构、Knockout等。</li>
<li>对于兼容性可用<a href="http://modernizr.com/">Modernizr</a>规范库辅助。</li>


</ul>
<h2 id="使用jshint"><a>使用jsHint</a></h2>
<ul>
<li>前端项目中推荐引入<a href="http://jshint.com/">jshint</a>插件来规范项目编码规范。以及一套完善的IDE配置。</li>
<li>注意：jshint需要引入nodejs 工具grunt或gulp插件，建议企业级nodejs npm私服。</li>


</ul>
<h2 id="前端工具"><a>前端工具</a></h2>
<ul>
<li>前端第三方JavaScript包管理工具bower(<code>bower install jQuery</code>)，bower可以实现第三方库的依赖解析、下载、升级管理等。建议建立企业级bower私服。</li>
<li>前端构建工具，可以采用grunt或者gulp工具，可以实现html、css、js压缩、验证、测试，文件合并、watch和liveload等所有前端任务。建议企业级nodejs npm私服。</li>
<li>前端开发IDE： WebStorm( Idea )、Sublime为最佳 。项目组统一IDE。IDE统一配置很重要。</li>
</ul>
</div>
</div>       
</body>