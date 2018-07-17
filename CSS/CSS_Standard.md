# CSS代码规范
  <div class="col">
    <ul>
      <li><a href="#css-syntax">语法</a></li>
      <li><a href="#css-declaration-order">声明顺序</a></li>
      <li><a href="#css-import">不要使用 @import</a></li>
      <li><a href="#css-media-queries">媒体查询（Media query）的位置</a></li>
      <li><a href="#css-prefixed-properties">带前缀的属性</a></li>
      <li><a href="#css-single-declarations">单行规则声明</a></li>
      <li><a href="#css-shorthand">简写形式的属性声明</a></li>
      <li><a href="#css-nesting">Less 和 Sass 中的嵌套</a></li>
      <li><a href="#css-operators">Less 和 Sass 中的操作符</a></li>
      <li><a href="#css-comments">注释</a></li>
      <li><a href="#css-classes">class 命名</a></li>
      <li><a href="#css-selectors">选择器</a></li>
      <li><a href="#css-organization">代码组织</a></li>
      <li><a href="#css-indentation">缩进</a></li>
        <li><a href="#css-semicolon">分号</a></li>
        <li><a href="#css-space">空格</a></li>
        <li><a href="#css-blank-line">空行</a></li>
        <li><a href="#css-new-line">换行</a></li>
        <li><a href="#css-comments">注释</a></li>
        <li><a href="#css-quote-marks">引号</a></li>
        <li><a href="#css-naming-rule">命名</a></li>
        <li><a href="#css-declaration-order">属性声明顺序</a></li>
        <li><a href="#css-color">颜色</a></li>
        <li><a href="#css-shorthand">属性简写</a></li>
        <li><a href="#css-media-queries">媒体查询</a></li>
        <li><a href="#css-scss">SCSS相关</a></li>
        <li><a href="#css-miscellaneous">杂项</a></li>
    </ul>

</div>

<div class="section" id="css-syntax">
  <div class="col">
    <h3>语法</h3>
    <ul>
      <li>用两个空格来代替制表符（tab） -- 这是唯一能保证在所有环境下获得一致展现的方法。</li>
      <li>为选择器分组时，将单独的选择器单独放在一行。</li>
      <li>为了代码的易读性，在每个声明块的左花括号前添加一个空格。</li>
      <li>声明块的右花括号应当单独成行。</li>
      <li>每条声明语句的 <code>:</code> 后应该插入一个空格。</li>
      <li>为了获得更准确的错误报告，每条声明都应该独占一行。</li>
      <li>所有声明语句都应当以分号结尾。最后一条声明语句后面的分号是可选的，但是，如果省略这个分号，你的代码可能更易出错。</li>
      <li>对于以逗号分隔的属性值，每个逗号后面都应该插入一个空格（例如，<code>box-shadow</code>）。</li>
      <li>不要在 <code>rgb()</code>、<code>rgba()</code>、<code>hsl()</code>、<code>hsla()</code> 或 <code>rect()</code> 值的<em>内部</em>的逗号后面插入空格。这样利于从多个属性值（既加逗号也加空格）中区分多个颜色值（只加逗号，不加空格）。</li>
      <li>对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，<code>.5</code> 代替 <code>0.5</code>；<code>-.5px</code> 代替 <code>-0.5px</code>）。</li>
      <li>十六进制值应该全部小写，例如，<code>#fff</code>。在扫描文档时，小写字符易于分辨，因为他们的形式更易于区分。</li>
      <li>尽量使用简写形式的十六进制值，例如，用 <code>#fff</code> 代替 <code>#ffffff</code>。</li>
      <li>为选择器中的属性添加双引号，例如，<code>input[type="text"]</code>。<a href="http://mathiasbynens.be/notes/unquoted-attribute-values#css">只有在某些情况下是可选的</a>，但是，为了代码的一致性，建议都加上双引号。</li>
      <li>避免为 0 值指定单位，例如，用 <code>margin: 0;</code> 代替 <code>margin: 0px;</code>。</li>
    </ul>
    <p>对于这里用到的术语有疑问吗？请参考 Wikipedia 上的 <a href="http://en.wikipedia.org/wiki/Cascading_Style_Sheets#Syntax">syntax section of the Cascading Style Sheets article</a>。</p>
  </div>
  <div class="col">
    <figure class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* Bad CSS */</span>
<span class="nc">.selector</span><span class="o">,</span> <span class="nc">.selector-secondary</span><span class="o">,</span> <span class="nc">.selector</span><span class="o">[</span><span class="nt">type</span><span class="o">=</span><span class="nt">text</span><span class="o">]</span> <span class="p">{</span>
  <span class="nl">padding</span><span class="p">:</span><span class="m">15px</span><span class="p">;</span>
  <span class="nl">margin</span><span class="p">:</span><span class="m">0px</span> <span class="m">0px</span> <span class="m">15px</span><span class="p">;</span>
  <span class="nl">background-color</span><span class="p">:</span><span class="n">rgba</span><span class="p">(</span><span class="m">0</span><span class="p">,</span> <span class="m">0</span><span class="p">,</span> <span class="m">0</span><span class="p">,</span> <span class="m">0.5</span><span class="p">);</span>
  <span class="nl">box-shadow</span><span class="p">:</span><span class="m">0px</span> <span class="m">1px</span> <span class="m">2px</span> <span class="m">#CCC</span><span class="p">,</span><span class="nb">inset</span> <span class="m">0</span> <span class="m">1px</span> <span class="m">0</span> <span class="m">#FFFFFF</span>
<span class="p">}</span>

<span class="c">/* Good CSS */</span>
<span class="nc">.selector</span><span class="o">,</span>
<span class="nc">.selector-secondary</span><span class="o">,</span>
<span class="nc">.selector</span><span class="o">[</span><span class="nt">type</span><span class="o">=</span><span class="s1">"text"</span><span class="o">]</span> <span class="p">{</span>
  <span class="nl">padding</span><span class="p">:</span> <span class="m">15px</span><span class="p">;</span>
  <span class="nl">margin-bottom</span><span class="p">:</span> <span class="m">15px</span><span class="p">;</span>
  <span class="nl">background-color</span><span class="p">:</span> <span class="n">rgba</span><span class="p">(</span><span class="m">0</span><span class="p">,</span><span class="m">0</span><span class="p">,</span><span class="m">0</span><span class="p">,</span><span class="m">.5</span><span class="p">);</span>
  <span class="nl">box-shadow</span><span class="p">:</span> <span class="m">0</span> <span class="m">1px</span> <span class="m">2px</span> <span class="m">#ccc</span><span class="p">,</span> <span class="nb">inset</span> <span class="m">0</span> <span class="m">1px</span> <span class="m">0</span> <span class="m">#fff</span><span class="p">;</span>
<span class="p">}</span></code></pre></figure>
  </div>
</div>

<div class="section" id="css-declaration-order">
  <div class="col">
    <h3>声明顺序</h3>
    <p>相关的属性声明应当归为一组，并按照下面的顺序排列：</p>
    <ol>
      <li>Positioning</li>
      <li>Box model</li>
      <li>Typographic</li>
      <li>Visual</li>
    </ol>
    <p>由于定位（positioning）可以从正常的文档流中移除元素，并且还能覆盖盒模型（box model）相关的样式，因此排在首位。盒模型排在第二位，因为它决定了组件的尺寸和位置。</p>
    <p>其他属性只是影响组件的<em>内部（inside）</em>或者是不影响前两组属性，因此排在后面。</p>
    <p>完整的属性列表及其排列顺序请参考 <a href="http://twitter.github.com/recess">Recess</a>。</p>
  </div>
  <div class="col">
    <figure class="highlight"><pre><code class="language-css" data-lang="css"><span class="nc">.declaration-order</span> <span class="p">{</span>
  <span class="c">/* Positioning */</span>
  <span class="nl">position</span><span class="p">:</span> <span class="nb">absolute</span><span class="p">;</span>
  <span class="nl">top</span><span class="p">:</span> <span class="m">0</span><span class="p">;</span>
  <span class="nl">right</span><span class="p">:</span> <span class="m">0</span><span class="p">;</span>
  <span class="nl">bottom</span><span class="p">:</span> <span class="m">0</span><span class="p">;</span>
  <span class="nl">left</span><span class="p">:</span> <span class="m">0</span><span class="p">;</span>
  <span class="nl">z-index</span><span class="p">:</span> <span class="m">100</span><span class="p">;</span>

  <span class="c">/* Box-model */</span>
  <span class="nl">display</span><span class="p">:</span> <span class="nb">block</span><span class="p">;</span>
  <span class="nl">float</span><span class="p">:</span> <span class="nb">right</span><span class="p">;</span>
  <span class="nl">width</span><span class="p">:</span> <span class="m">100px</span><span class="p">;</span>
  <span class="nl">height</span><span class="p">:</span> <span class="m">100px</span><span class="p">;</span>

  <span class="c">/* Typography */</span>
  <span class="nl">font</span><span class="p">:</span> <span class="nb">normal</span> <span class="m">13px</span> <span class="s1">"Helvetica Neue"</span><span class="p">,</span> <span class="nb">sans-serif</span><span class="p">;</span>
  <span class="nl">line-height</span><span class="p">:</span> <span class="m">1.5</span><span class="p">;</span>
  <span class="nl">color</span><span class="p">:</span> <span class="m">#333</span><span class="p">;</span>
  <span class="nl">text-align</span><span class="p">:</span> <span class="nb">center</span><span class="p">;</span>

  <span class="c">/* Visual */</span>
  <span class="nl">background-color</span><span class="p">:</span> <span class="m">#f5f5f5</span><span class="p">;</span>
  <span class="nl">border</span><span class="p">:</span> <span class="m">1px</span> <span class="nb">solid</span> <span class="m">#e5e5e5</span><span class="p">;</span>
  <span class="nl">border-radius</span><span class="p">:</span> <span class="m">3px</span><span class="p">;</span>

  <span class="c">/* Misc */</span>
  <span class="nl">opacity</span><span class="p">:</span> <span class="m">1</span><span class="p">;</span>
<span class="p">}</span></code></pre></figure>
  </div>
</div>

<div class="section" id="css-import">
  <div class="col">
    <h3>不要使用 <code>@import</code></h3>
    <p>与 <code>&lt;link&gt;</code> 标签相比，<code>@import</code> 指令要慢很多，不光增加了额外的请求次数，还会导致不可预料的问题。替代办法有以下几种：</p>
    <ul>
      <li>使用多个 <code>&lt;link&gt;</code> 元素</li>
      <li>通过 Sass 或 Less 类似的 CSS 预处理器将多个 CSS 文件编译为一个文件</li>
      <li>通过 Rails、Jekyll 或其他系统中提供过 CSS 文件合并功能</li>
    </ul>
    <p>请参考 <a href="http://www.stevesouders.com/blog/2009/04/09/dont-use-import/">Steve Souders 的文章</a>了解更多知识。</p>
  </div>
  <div class="col">
    <figure class="highlight"><pre><code class="language-html" data-lang="html"><span class="c">&lt;!-- Use link elements --&gt;</span>
<span class="nt">&lt;link</span> <span class="na">rel=</span><span class="s">"stylesheet"</span> <span class="na">href=</span><span class="s">"core.css"</span><span class="nt">&gt;</span>

<span class="c">&lt;!-- Avoid @imports --&gt;</span>
<span class="nt">&lt;style&gt;</span>
  <span class="k">@import</span> <span class="sx">url("more.css")</span><span class="p">;</span>
<span class="nt">&lt;/style&gt;</span></code></pre></figure>
  </div>
</div>

<div class="section" id="css-media-queries">
  <div class="col">
    <h3>媒体查询（Media query）的位置</h3>
    <p>将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部。如果你把他们分开了，将来只会被大家遗忘。下面给出一个典型的实例。</p>
  </div>
  <div class="col">
    <figure class="highlight"><pre><code class="language-css" data-lang="css"><span class="nc">.element</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>
<span class="nc">.element-avatar</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>
<span class="nc">.element-selected</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>

<span class="k">@media</span> <span class="p">(</span><span class="n">min-width</span><span class="p">:</span> <span class="m">480px</span><span class="p">)</span> <span class="p">{</span>
  <span class="nc">.element</span> <span class="p">{</span> <span class="err">...</span><span class="p">}</span>
  <span class="nc">.element-avatar</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>
  <span class="nc">.element-selected</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>
<span class="p">}</span></code></pre></figure>
  </div>
</div>

<div class="section" id="css-prefixed-properties">
  <div class="col">
    <h3>带前缀的属性</h3>
    <p>当使用特定厂商的带有前缀的属性时，通过缩进的方式，让每个属性的值在垂直方向对齐，这样便于多行编辑。</p>
    <p>在 Textmate 中，使用 <strong>Text → Edit Each Line in Selection</strong> (⌃⌘A)。在 Sublime Text 2 中，使用 <strong>Selection → Add Previous Line</strong> (⌃⇧↑) 和 <strong>Selection →  Add Next Line</strong> (⌃⇧↓)。</p>
  </div>
  <div class="col">
    <figure class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* Prefixed properties */</span>
<span class="nc">.selector</span> <span class="p">{</span>
  <span class="nl">-webkit-box-shadow</span><span class="p">:</span> <span class="m">0</span> <span class="m">1px</span> <span class="m">2px</span> <span class="n">rgba</span><span class="p">(</span><span class="m">0</span><span class="p">,</span><span class="m">0</span><span class="p">,</span><span class="m">0</span><span class="p">,</span><span class="m">.15</span><span class="p">);</span>
          <span class="nl">box-shadow</span><span class="p">:</span> <span class="m">0</span> <span class="m">1px</span> <span class="m">2px</span> <span class="n">rgba</span><span class="p">(</span><span class="m">0</span><span class="p">,</span><span class="m">0</span><span class="p">,</span><span class="m">0</span><span class="p">,</span><span class="m">.15</span><span class="p">);</span>
<span class="p">}</span></code></pre></figure>
  </div>
</div>

<div class="section" id="css-single-declarations">
  <div class="col">
    <h3>单行规则声明</h3>
    <p>对于<strong>只包含一条声明</strong>的样式，为了易读性和便于快速编辑，建议将语句放在同一行。对于带有多条声明的样式，还是应当将声明分为多行。</p>
    <p>这样做的关键因素是为了错误检测 -- 例如，CSS 校验器指出在 183 行有语法错误。如果是单行单条声明，你就不会忽略这个错误；如果是单行多条声明的话，你就要仔细分析避免漏掉错误了。</p>
  </div>
  <div class="col">
    <figure class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* Single declarations on one line */</span>
<span class="nc">.span1</span> <span class="p">{</span> <span class="nl">width</span><span class="p">:</span> <span class="m">60px</span><span class="p">;</span> <span class="p">}</span>
<span class="nc">.span2</span> <span class="p">{</span> <span class="nl">width</span><span class="p">:</span> <span class="m">140px</span><span class="p">;</span> <span class="p">}</span>
<span class="nc">.span3</span> <span class="p">{</span> <span class="nl">width</span><span class="p">:</span> <span class="m">220px</span><span class="p">;</span> <span class="p">}</span>

<span class="c">/* Multiple declarations, one per line */</span>
<span class="nc">.sprite</span> <span class="p">{</span>
  <span class="nl">display</span><span class="p">:</span> <span class="n">inline-block</span><span class="p">;</span>
  <span class="nl">width</span><span class="p">:</span> <span class="m">16px</span><span class="p">;</span>
  <span class="nl">height</span><span class="p">:</span> <span class="m">15px</span><span class="p">;</span>
  <span class="nl">background-image</span><span class="p">:</span> <span class="sx">url(../img/sprite.png)</span><span class="p">;</span>
<span class="p">}</span>
<span class="nc">.icon</span>           <span class="p">{</span> <span class="nl">background-position</span><span class="p">:</span> <span class="m">0</span> <span class="m">0</span><span class="p">;</span> <span class="p">}</span>
<span class="nc">.icon-home</span>      <span class="p">{</span> <span class="nl">background-position</span><span class="p">:</span> <span class="m">0</span> <span class="m">-20px</span><span class="p">;</span> <span class="p">}</span>
<span class="nc">.icon-account</span>   <span class="p">{</span> <span class="nl">background-position</span><span class="p">:</span> <span class="m">0</span> <span class="m">-40px</span><span class="p">;</span> <span class="p">}</span></code></pre></figure>
  </div>
</div>

<div class="section" id="css-shorthand">
  <div class="col">
    <h3>简写形式的属性声明</h3>
    <p>在需要显示地设置所有值的情况下，应当尽量限制使用简写形式的属性声明。常见的滥用简写属性声明的情况如下：</p>
    <ul>
      <li><code>padding</code></li>
      <li><code>margin</code></li>
      <li><code>font</code></li>
      <li><code>background</code></li>
      <li><code>border</code></li>
      <li><code>border-radius</code></li>
    </ul>
    <p>大部分情况下，我们不需要为简写形式的属性声明指定所有值。例如，HTML 的 heading 元素只需要设置上、下边距（margin）的值，因此，在必要的时候，只需覆盖这两个值就可以。过度使用简写形式的属性声明会导致代码混乱，并且会对属性值带来不必要的覆盖从而引起意外的副作用。</p>
    <p>在 MDN（Mozilla Developer Network）上一篇非常好的关于<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties">shorthand properties</a> 的文章，对于不太熟悉简写属性声明及其行为的用户很有用。</p>
  </div>
  <div class="col">
    <figure class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* Bad example */</span>
<span class="nc">.element</span> <span class="p">{</span>
  <span class="nl">margin</span><span class="p">:</span> <span class="m">0</span> <span class="m">0</span> <span class="m">10px</span><span class="p">;</span>
  <span class="nl">background</span><span class="p">:</span> <span class="no">red</span><span class="p">;</span>
  <span class="nl">background</span><span class="p">:</span> <span class="sx">url("image.jpg")</span><span class="p">;</span>
  <span class="nl">border-radius</span><span class="p">:</span> <span class="m">3px</span> <span class="m">3px</span> <span class="m">0</span> <span class="m">0</span><span class="p">;</span>
<span class="p">}</span>

<span class="c">/* Good example */</span>
<span class="nc">.element</span> <span class="p">{</span>
  <span class="nl">margin-bottom</span><span class="p">:</span> <span class="m">10px</span><span class="p">;</span>
  <span class="nl">background-color</span><span class="p">:</span> <span class="no">red</span><span class="p">;</span>
  <span class="nl">background-image</span><span class="p">:</span> <span class="sx">url("image.jpg")</span><span class="p">;</span>
  <span class="nl">border-top-left-radius</span><span class="p">:</span> <span class="m">3px</span><span class="p">;</span>
  <span class="nl">border-top-right-radius</span><span class="p">:</span> <span class="m">3px</span><span class="p">;</span>
<span class="p">}</span></code></pre></figure>
  </div>
</div>

<div class="section" id="css-nesting">
  <div class="col">
    <h3>Less 和 Sass 中的嵌套</h3>
    <p>避免不必要的嵌套。这是因为虽然你可以使用嵌套，但是并不意味着应该使用嵌套。只有在必须将样式限制在父元素内（也就是后代选择器），并且存在多个需要嵌套的元素时才使用嵌套。</p>
    <p>扩展阅读：</p>
    <ul>
      <li><a href="http://markdotto.com/2015/07/20/css-nesting/">Nesting in Sass and Less</a></li>
    </ul>
  </div>
  <div class="col">
    <figure class="highlight"><pre><code class="language-scss" data-lang="scss"><span class="c1">// Without nesting</span>
<span class="nc">.table</span> <span class="o">&gt;</span> <span class="nt">thead</span> <span class="o">&gt;</span> <span class="nt">tr</span> <span class="o">&gt;</span> <span class="nt">th</span> <span class="p">{</span> <span class="err">…</span> <span class="p">}</span>
<span class="nc">.table</span> <span class="o">&gt;</span> <span class="nt">thead</span> <span class="o">&gt;</span> <span class="nt">tr</span> <span class="o">&gt;</span> <span class="nt">td</span> <span class="p">{</span> <span class="err">…</span> <span class="p">}</span>

<span class="c1">// With nesting</span>
<span class="nc">.table</span> <span class="o">&gt;</span> <span class="nt">thead</span> <span class="o">&gt;</span> <span class="nt">tr</span> <span class="p">{</span>
  <span class="o">&gt;</span> <span class="nt">th</span> <span class="p">{</span> <span class="err">…</span> <span class="p">}</span>
  <span class="o">&gt;</span> <span class="nt">td</span> <span class="p">{</span> <span class="err">…</span> <span class="p">}</span>
<span class="p">}</span></code></pre></figure>
  </div>
</div>

<div class="section" id="css-operators">
  <div class="col">
    <h3>Less 和 Sass 中的操作符</h3>
    <p>为了提高可读性，在圆括号中的数学计算表达式的数值、变量和操作符之间均添加一个空格。</p>
  </div>
  <div class="col">
    <figure class="highlight"><pre><code class="language-scss" data-lang="scss"><span class="c1">// Bad example</span>
<span class="nc">.element</span> <span class="p">{</span>
  <span class="nl">margin</span><span class="p">:</span> <span class="m">10px</span> <span class="m">0</span> <span class="o">@</span><span class="n">variable</span><span class="o">*</span><span class="m">2</span> <span class="m">10px</span><span class="p">;</span>
<span class="p">}</span>

<span class="c1">// Good example</span>
<span class="nc">.element</span> <span class="p">{</span>
  <span class="nl">margin</span><span class="p">:</span> <span class="m">10px</span> <span class="nf">0</span> <span class="p">(</span><span class="o">@</span><span class="n">variable</span> <span class="o">*</span> <span class="m">2</span><span class="p">)</span> <span class="m">10px</span><span class="p">;</span>
<span class="p">}</span></code></pre></figure>
  </div>
</div>

<div class="section" id="css-comments">
  <div class="col">
    <h3>注释</h3>
    <p>代码是由人编写并维护的。请确保你的代码能够自描述、注释良好并且易于他人理解。好的代码注释能够传达上下文关系和代码目的。不要简单地重申组件或 class 名称。</p>
    <p>对于较长的注释，务必书写完整的句子；对于一般性注解，可以书写简洁的短语。</p>
  </div>
  <div class="col">
    <figure class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* Bad example */</span>
<span class="c">/* Modal header */</span>
<span class="nc">.modal-header</span> <span class="p">{</span>
  <span class="err">...</span>
<span class="p">}</span>

<span class="c">/* Good example */</span>
<span class="c">/* Wrapping element for .modal-title and .modal-close */</span>
<span class="nc">.modal-header</span> <span class="p">{</span>
  <span class="err">...</span>
<span class="p">}</span></code></pre></figure>
  </div>
</div>

<div class="section" id="css-classes">
  <div class="col">
    <h3>class 命名</h3>
    <ul>
      <li>class 名称中只能出现小写字符和破折号（dashe）（不是下划线，也不是驼峰命名法）。破折号应当用于相关 class 的命名（类似于命名空间）（例如，<code>.btn</code> 和 <code>.btn-danger</code>）。</li>
      <li>避免过度任意的简写。<code>.btn</code> 代表 <em>button</em>，但是 <code>.s</code> 不能表达任何意思。</li>
      <li>class 名称应当尽可能短，并且意义明确。</li>
      <li>使用有意义的名称。使用有组织的或目的明确的名称，不要使用表现形式（presentational）的名称。</li>
      <li>基于最近的父 class 或基本（base） class 作为新 class 的前缀。</li>
      <li>使用 <code>.js-*</code> class 来标识行为（与样式相对），并且不要将这些 class 包含到 CSS 文件中。</li>
    </ul>
    <p>在为 Sass 和 Less 变量命名时也可以参考上面列出的各项规范。</p>
  </div>
  <div class="col">
    <figure class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* Bad example */</span>
<span class="nc">.t</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>
<span class="nc">.red</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>
<span class="nc">.header</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>

<span class="c">/* Good example */</span>
<span class="nc">.tweet</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>
<span class="nc">.important</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>
<span class="nc">.tweet-header</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span></code></pre></figure>
  </div>
</div>

<div class="section" id="css-selectors">
  <div class="col">
    <h3>选择器</h3>
    <ul>
      <li>对于通用元素使用 class ，这样利于渲染性能的优化。</li>
      <li>对于经常出现的组件，避免使用属性选择器（例如，<code>[class^="..."]</code>）。浏览器的性能会受到这些因素的影响。</li>
      <li>选择器要尽可能短，并且尽量限制组成选择器的元素个数，建议不要超过 3 。</li>
      <li><strong>只有</strong>在必要的时候才将 class 限制在最近的父元素内（也就是后代选择器）（例如，不使用带前缀的 class 时 -- 前缀类似于命名空间）。</li>
    </ul>
    <p>扩展阅读：</p>
    <ul>
      <li><a href="http://markdotto.com/2012/02/16/scope-css-classes-with-prefixes/">Scope CSS classes with prefixes</a></li>
      <li><a href="http://markdotto.com/2012/03/02/stop-the-cascade/">Stop the cascade</a></li>
    </ul>
  </div>
  <div class="col">
    <figure class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* Bad example */</span>
<span class="nt">span</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>
<span class="nc">.page-container</span> <span class="nf">#stream</span> <span class="nc">.stream-item</span> <span class="nc">.tweet</span> <span class="nc">.tweet-header</span> <span class="nc">.username</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>
<span class="nc">.avatar</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>

<span class="c">/* Good example */</span>
<span class="nc">.avatar</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>
<span class="nc">.tweet-header</span> <span class="nc">.username</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>
<span class="nc">.tweet</span> <span class="nc">.avatar</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span></code></pre></figure>
  </div>
</div>

<div class="section" id="css-organization">
  <div class="col">
    <h3>代码组织</h3>
    <ul>
      <li>以组件为单位组织代码段。</li>
      <li>制定一致的注释规范。</li>
      <li>使用一致的空白符将代码分隔成块，这样利于扫描较大的文档。</li>
      <li>如果使用了多个 CSS 文件，将其按照组件而非页面的形式分拆，因为页面会被重组，而组件只会被移动。</li>
    </ul>
  </div>
  <div class="col">
    <figure class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/*
 * Component section heading
 */</span>

<span class="nc">.element</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>


<span class="c">/*
 * Component section heading
 *
 * Sometimes you need to include optional context for the entire component. Do that up here if it's important enough.
 */</span>

<span class="nc">.element</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span>

<span class="c">/* Contextual sub-component or modifer */</span>
<span class="nc">.element-heading</span> <span class="p">{</span> <span class="err">...</span> <span class="p">}</span></code></pre></figure>
  </div>
</div>

<div class="section" id="css-indentation">
    <div class="col">
        <h3>缩进</h3>
        <p>使用soft tab（4个空格）。</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-css" data-lang="css"><span class="nc">.element</span> <span class="p">{</span>
    <span class="k">position</span><span class="o">:</span> <span class="k">absolute</span><span class="p">;</span>
    <span class="k">top</span><span class="o">:</span> <span class="m">10px</span><span class="p">;</span>
    <span class="k">left</span><span class="o">:</span> <span class="m">10px</span><span class="p">;</span>

    <span class="k">border</span><span class="o">-</span><span class="n">radius</span><span class="o">:</span> <span class="m">10px</span><span class="p">;</span>
    <span class="k">width</span><span class="o">:</span> <span class="m">50px</span><span class="p">;</span>
    <span class="k">height</span><span class="o">:</span> <span class="m">50px</span><span class="p">;</span>
<span class="p">}</span></code></pre></div>
    </div>
</div>

<div class="section" id="css-semicolon">
    <div class="col">
        <h3>分号</h3>
        <p>每个属性声明末尾都要加分号。</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-css" data-lang="css"><span class="nc">.element</span> <span class="p">{</span>
    <span class="k">width</span><span class="o">:</span> <span class="m">20px</span><span class="p">;</span>
    <span class="k">height</span><span class="o">:</span> <span class="m">20px</span><span class="p">;</span>

    <span class="k">background-color</span><span class="o">:</span> <span class="nb">red</span><span class="p">;</span>
<span class="p">}</span></code></pre></div>
    </div>
</div>

<div class="section" id="css-space">
    <div class="col">
        <h3>空格</h3>
        <p>以下几种情况不需要空格：</p>
        <ul>
            <li>属性名后</li>
            <li>多个规则的分隔符','前</li>
            <li><code>!important</code> '!'后</li>
            <li>属性值中'('后和')'前</li>
            <li>行末不要有多余的空格</li>
        </ul>
        <p>以下几种情况需要空格：</p>
        <ul>
            <li>属性值前</li>
            <li>选择器'&gt;', '+', '~'前后</li>
            <li>'{'前</li>
            <li><code>!important</code> '!'前</li>
            <li><code>@else</code> 前后</li>
            <li>属性值中的','后</li>
            <li>注释'/*'后和'*/'前</li>
        </ul>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* not good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="k">color</span> <span class="o">:</span><span class="nb">red</span><span class="o">!</span> <span class="n">important</span><span class="p">;</span>
    <span class="k">background-color</span><span class="o">:</span> <span class="n">rgba</span><span class="p">(</span><span class="m">0</span><span class="o">,</span><span class="m">0</span><span class="o">,</span><span class="m">0</span><span class="o">,.</span><span class="m">5</span><span class="p">);</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="k">color</span><span class="o">:</span> <span class="nb">red</span> <span class="cp">!important</span><span class="p">;</span>
    <span class="k">background-color</span><span class="o">:</span> <span class="n">rgba</span><span class="p">(</span><span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="o">,</span> <span class="o">.</span><span class="m">5</span><span class="p">);</span>
<span class="p">}</span>

<span class="c">/* not good */</span>
<span class="nc">.element</span> <span class="o">,</span>
<span class="nc">.dialog</span><span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span><span class="o">,</span>
<span class="nc">.dialog</span> <span class="p">{</span>

<span class="p">}</span>

<span class="c">/* not good */</span>
<span class="nc">.element</span><span class="o">&gt;</span><span class="nc">.dialog</span><span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span> <span class="o">&gt;</span> <span class="nc">.dialog</span><span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="c">/* not good */</span>
<span class="nc">.element</span><span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="c">/* not good */</span>
<span class="k">@if</span><span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span><span class="k">@else</span><span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="k">@if</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span> <span class="k">@else</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span></code></pre></div>
    </div>
</div>

<div class="section" id="css-blank-line">
    <div class="col">
        <h3>空行</h3>
        <p>以下几种情况需要空行：</p>
        <ul>
            <li>文件最后保留一个空行</li>
            <li>'}'后最好跟一个空行，包括scss中嵌套的规则</li>
            <li>属性之间需要适当的空行，具体见<a href="#css-declaration-order">属性声明顺序</a></li>
        </ul>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* not good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>
<span class="nc">.dialog</span> <span class="p">{</span>
    <span class="k">color</span><span class="o">:</span> <span class="nb">red</span><span class="p">;</span>
    <span class="o">&amp;:</span><span class="n">after</span> <span class="err">{</span>
        <span class="o">...</span>
    <span class="p">}</span>
<span class="err">}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="nc">.dialog</span> <span class="p">{</span>
    <span class="k">color</span><span class="o">:</span> <span class="nb">red</span><span class="p">;</span>

    <span class="o">&amp;:</span><span class="n">after</span> <span class="err">{</span>
        <span class="o">...</span>
    <span class="p">}</span>
<span class="err">}</span></code></pre></div>
    </div>
</div>

<div class="section" id="css-new-line">
    <div class="col">
        <h3>换行</h3>
        <p>以下几种情况不需要换行：</p>
        <ul>
            <li>'{'前</li>
        </ul>
        <p>以下几种情况需要换行：</p>
        <ul>
            <li>'{'后和'}'前</li>
            <li>每个属性独占一行</li>
            <li>多个规则的分隔符','后</li>
        </ul>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* not good */</span>
<span class="nc">.element</span>
<span class="p">{</span><span class="k">color</span><span class="o">:</span> <span class="nb">red</span><span class="p">;</span> <span class="k">background-color</span><span class="o">:</span> <span class="nb">black</span><span class="p">;}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="k">color</span><span class="o">:</span> <span class="nb">red</span><span class="p">;</span>
    <span class="k">background-color</span><span class="o">:</span> <span class="nb">black</span><span class="p">;</span>
<span class="p">}</span>

<span class="c">/* not good */</span>
<span class="nc">.element</span><span class="o">,</span> <span class="nc">.dialog</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span><span class="o">,</span>
<span class="nc">.dialog</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span></code></pre></div>
    </div>
</div>

<div class="section" id="css-comments">
    <div class="col">
        <h3>注释</h3>
        <p>注释统一用'/* */'（scss中也不要用'//'），具体参照右边的写法；</p>
        <p>缩进与下一行代码保持一致；</p>
        <p>可位于一个代码行的末尾，与代码间隔一个空格。
    </p></div>
    <div class="col">
        <div class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* Modal header */</span>
<span class="nc">.modal-header</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="c">/*</span>
<span class="c"> * Modal header</span>
<span class="c"> */</span>
<span class="nc">.modal-header</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="nc">.modal-header</span> <span class="p">{</span>
    <span class="c">/* 50px */</span>
    <span class="k">width</span><span class="o">:</span> <span class="m">50px</span><span class="p">;</span>

    <span class="k">color</span><span class="o">:</span> <span class="nb">red</span><span class="p">;</span> <span class="c">/* color red */</span>
<span class="p">}</span></code></pre></div>
    </div>
</div>

<div class="section" id="css-quote-marks">
    <div class="col">
        <h3>引号</h3>
        <p>最外层统一使用双引号；</p>
        <p>url的内容要用引号；</p>
        <p>属性选择器中的属性值需要引号。</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-css" data-lang="css"><span class="nc">.element</span><span class="nd">:after</span> <span class="p">{</span>
    <span class="k">content</span><span class="o">:</span> <span class="s2">""</span><span class="p">;</span>
    <span class="k">background-image</span><span class="o">:</span> <span class="sx">url("logo.png")</span><span class="p">;</span>
<span class="p">}</span>

<span class="nt">li</span><span class="o">[</span><span class="nt">data-type</span><span class="o">=</span><span class="s2">"single"</span><span class="o">]</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span></code></pre></div>
    </div>
</div>

<div class="section" id="css-naming-rule">
    <div class="col">
        <h3>命名</h3>
        <ul>
            <li>类名使用小写字母，以中划线分隔</li>
            <li>id采用驼峰式命名</li>
            <li>scss中的变量、函数、混合、placeholder采用驼峰式命名</li>
        </ul>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* class */</span>
<span class="nc">.element-content</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="c">/* id */</span>
<span class="nf">#myDialog</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="c">/* 变量 */</span>
<span class="o">$</span><span class="nt">colorBlack</span><span class="o">:</span> <span class="nf">#000</span><span class="o">;</span>

<span class="c">/* 函数 */</span>
<span class="k">@function</span> <span class="nt">pxToRem</span><span class="o">($</span><span class="nt">px</span><span class="o">)</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="c">/* 混合 */</span>
<span class="k">@mixin</span> <span class="nt">centerBlock</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="c">/* placeholder */</span>
<span class="o">%</span><span class="nt">myDialog</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span></code></pre></div>
    </div>
</div>

<div class="section" id="css-declaration-order">
    <div class="col">
        <h3>属性声明顺序</h3>
        <p>相关的属性声明按右边的顺序做分组处理，组之间需要有一个空行。</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-css" data-lang="css"><span class="nc">.declaration-order</span> <span class="p">{</span>
    <span class="k">display</span><span class="o">:</span> <span class="k">block</span><span class="p">;</span>
    <span class="k">float</span><span class="o">:</span> <span class="k">right</span><span class="p">;</span>

    <span class="k">position</span><span class="o">:</span> <span class="k">absolute</span><span class="p">;</span>
    <span class="k">top</span><span class="o">:</span> <span class="m">0</span><span class="p">;</span>
    <span class="k">right</span><span class="o">:</span> <span class="m">0</span><span class="p">;</span>
    <span class="k">bottom</span><span class="o">:</span> <span class="m">0</span><span class="p">;</span>
    <span class="k">left</span><span class="o">:</span> <span class="m">0</span><span class="p">;</span>
    <span class="k">z-index</span><span class="o">:</span> <span class="m">100</span><span class="p">;</span>

    <span class="k">border</span><span class="o">:</span> <span class="m">1px</span> <span class="k">solid</span> <span class="m">#e5e5e5</span><span class="p">;</span>
    <span class="k">border</span><span class="o">-</span><span class="n">radius</span><span class="o">:</span> <span class="m">3px</span><span class="p">;</span>
    <span class="k">width</span><span class="o">:</span> <span class="m">100px</span><span class="p">;</span>
    <span class="k">height</span><span class="o">:</span> <span class="m">100px</span><span class="p">;</span>

    <span class="k">font</span><span class="o">:</span> <span class="k">normal</span> <span class="m">13px</span> <span class="s2">"Helvetica Neue"</span><span class="o">,</span> <span class="k">sans-serif</span><span class="p">;</span>
    <span class="k">line-height</span><span class="o">:</span> <span class="m">1</span><span class="o">.</span><span class="m">5</span><span class="p">;</span>
    <span class="k">text-align</span><span class="o">:</span> <span class="k">center</span><span class="p">;</span>

    <span class="k">color</span><span class="o">:</span> <span class="m">#333</span><span class="p">;</span>
    <span class="k">background-color</span><span class="o">:</span> <span class="m">#f5f5f5</span><span class="p">;</span>

    <span class="k">opacity</span><span class="o">:</span> <span class="m">1</span><span class="p">;</span>
<span class="p">}</span></code></pre></div>
        <div class="highlight"><pre><code class="language-javascript" data-lang="javascript"><span class="c1">// 下面是推荐的属性的顺序</span>
<span class="p">[</span>
    <span class="p">[</span>
        <span class="s2">"display"</span><span class="p">,</span>
        <span class="s2">"visibility"</span><span class="p">,</span>
        <span class="s2">"float"</span><span class="p">,</span>
        <span class="s2">"clear"</span><span class="p">,</span>
        <span class="s2">"overflow"</span><span class="p">,</span>
        <span class="s2">"overflow-x"</span><span class="p">,</span>
        <span class="s2">"overflow-y"</span><span class="p">,</span>
        <span class="s2">"clip"</span><span class="p">,</span>
        <span class="s2">"zoom"</span>
    <span class="p">],</span>
    <span class="p">[</span>
        <span class="s2">"table-layout"</span><span class="p">,</span>
        <span class="s2">"empty-cells"</span><span class="p">,</span>
        <span class="s2">"caption-side"</span><span class="p">,</span>
        <span class="s2">"border-spacing"</span><span class="p">,</span>
        <span class="s2">"border-collapse"</span><span class="p">,</span>
        <span class="s2">"list-style"</span><span class="p">,</span>
        <span class="s2">"list-style-position"</span><span class="p">,</span>
        <span class="s2">"list-style-type"</span><span class="p">,</span>
        <span class="s2">"list-style-image"</span>
    <span class="p">],</span>
    <span class="p">[</span>
        <span class="s2">"-webkit-box-orient"</span><span class="p">,</span>
        <span class="s2">"-webkit-box-direction"</span><span class="p">,</span>
        <span class="s2">"-webkit-box-decoration-break"</span><span class="p">,</span>
        <span class="s2">"-webkit-box-pack"</span><span class="p">,</span>
        <span class="s2">"-webkit-box-align"</span><span class="p">,</span>
        <span class="s2">"-webkit-box-flex"</span>
    <span class="p">],</span>
    <span class="p">[</span>
        <span class="s2">"position"</span><span class="p">,</span>
        <span class="s2">"top"</span><span class="p">,</span>
        <span class="s2">"right"</span><span class="p">,</span>
        <span class="s2">"bottom"</span><span class="p">,</span>
        <span class="s2">"left"</span><span class="p">,</span>
        <span class="s2">"z-index"</span>
    <span class="p">],</span>
    <span class="p">[</span>
        <span class="s2">"margin"</span><span class="p">,</span>
        <span class="s2">"margin-top"</span><span class="p">,</span>
        <span class="s2">"margin-right"</span><span class="p">,</span>
        <span class="s2">"margin-bottom"</span><span class="p">,</span>
        <span class="s2">"margin-left"</span><span class="p">,</span>
        <span class="s2">"-webkit-box-sizing"</span><span class="p">,</span>
        <span class="s2">"-moz-box-sizing"</span><span class="p">,</span>
        <span class="s2">"box-sizing"</span><span class="p">,</span>
        <span class="s2">"border"</span><span class="p">,</span>
        <span class="s2">"border-width"</span><span class="p">,</span>
        <span class="s2">"border-style"</span><span class="p">,</span>
        <span class="s2">"border-color"</span><span class="p">,</span>
        <span class="s2">"border-top"</span><span class="p">,</span>
        <span class="s2">"border-top-width"</span><span class="p">,</span>
        <span class="s2">"border-top-style"</span><span class="p">,</span>
        <span class="s2">"border-top-color"</span><span class="p">,</span>
        <span class="s2">"border-right"</span><span class="p">,</span>
        <span class="s2">"border-right-width"</span><span class="p">,</span>
        <span class="s2">"border-right-style"</span><span class="p">,</span>
        <span class="s2">"border-right-color"</span><span class="p">,</span>
        <span class="s2">"border-bottom"</span><span class="p">,</span>
        <span class="s2">"border-bottom-width"</span><span class="p">,</span>
        <span class="s2">"border-bottom-style"</span><span class="p">,</span>
        <span class="s2">"border-bottom-color"</span><span class="p">,</span>
        <span class="s2">"border-left"</span><span class="p">,</span>
        <span class="s2">"border-left-width"</span><span class="p">,</span>
        <span class="s2">"border-left-style"</span><span class="p">,</span>
        <span class="s2">"border-left-color"</span><span class="p">,</span>
        <span class="s2">"-webkit-border-radius"</span><span class="p">,</span>
        <span class="s2">"-moz-border-radius"</span><span class="p">,</span>
        <span class="s2">"border-radius"</span><span class="p">,</span>
        <span class="s2">"-webkit-border-top-left-radius"</span><span class="p">,</span>
        <span class="s2">"-moz-border-radius-topleft"</span><span class="p">,</span>
        <span class="s2">"border-top-left-radius"</span><span class="p">,</span>
        <span class="s2">"-webkit-border-top-right-radius"</span><span class="p">,</span>
        <span class="s2">"-moz-border-radius-topright"</span><span class="p">,</span>
        <span class="s2">"border-top-right-radius"</span><span class="p">,</span>
        <span class="s2">"-webkit-border-bottom-right-radius"</span><span class="p">,</span>
        <span class="s2">"-moz-border-radius-bottomright"</span><span class="p">,</span>
        <span class="s2">"border-bottom-right-radius"</span><span class="p">,</span>
        <span class="s2">"-webkit-border-bottom-left-radius"</span><span class="p">,</span>
        <span class="s2">"-moz-border-radius-bottomleft"</span><span class="p">,</span>
        <span class="s2">"border-bottom-left-radius"</span><span class="p">,</span>
        <span class="s2">"-webkit-border-image"</span><span class="p">,</span>
        <span class="s2">"-moz-border-image"</span><span class="p">,</span>
        <span class="s2">"-o-border-image"</span><span class="p">,</span>
        <span class="s2">"border-image"</span><span class="p">,</span>
        <span class="s2">"-webkit-border-image-source"</span><span class="p">,</span>
        <span class="s2">"-moz-border-image-source"</span><span class="p">,</span>
        <span class="s2">"-o-border-image-source"</span><span class="p">,</span>
        <span class="s2">"border-image-source"</span><span class="p">,</span>
        <span class="s2">"-webkit-border-image-slice"</span><span class="p">,</span>
        <span class="s2">"-moz-border-image-slice"</span><span class="p">,</span>
        <span class="s2">"-o-border-image-slice"</span><span class="p">,</span>
        <span class="s2">"border-image-slice"</span><span class="p">,</span>
        <span class="s2">"-webkit-border-image-width"</span><span class="p">,</span>
        <span class="s2">"-moz-border-image-width"</span><span class="p">,</span>
        <span class="s2">"-o-border-image-width"</span><span class="p">,</span>
        <span class="s2">"border-image-width"</span><span class="p">,</span>
        <span class="s2">"-webkit-border-image-outset"</span><span class="p">,</span>
        <span class="s2">"-moz-border-image-outset"</span><span class="p">,</span>
        <span class="s2">"-o-border-image-outset"</span><span class="p">,</span>
        <span class="s2">"border-image-outset"</span><span class="p">,</span>
        <span class="s2">"-webkit-border-image-repeat"</span><span class="p">,</span>
        <span class="s2">"-moz-border-image-repeat"</span><span class="p">,</span>
        <span class="s2">"-o-border-image-repeat"</span><span class="p">,</span>
        <span class="s2">"border-image-repeat"</span><span class="p">,</span>
        <span class="s2">"padding"</span><span class="p">,</span>
        <span class="s2">"padding-top"</span><span class="p">,</span>
        <span class="s2">"padding-right"</span><span class="p">,</span>
        <span class="s2">"padding-bottom"</span><span class="p">,</span>
        <span class="s2">"padding-left"</span><span class="p">,</span>
        <span class="s2">"width"</span><span class="p">,</span>
        <span class="s2">"min-width"</span><span class="p">,</span>
        <span class="s2">"max-width"</span><span class="p">,</span>
        <span class="s2">"height"</span><span class="p">,</span>
        <span class="s2">"min-height"</span><span class="p">,</span>
        <span class="s2">"max-height"</span>
    <span class="p">],</span>
    <span class="p">[</span>
        <span class="s2">"font"</span><span class="p">,</span>
        <span class="s2">"font-family"</span><span class="p">,</span>
        <span class="s2">"font-size"</span><span class="p">,</span>
        <span class="s2">"font-weight"</span><span class="p">,</span>
        <span class="s2">"font-style"</span><span class="p">,</span>
        <span class="s2">"font-variant"</span><span class="p">,</span>
        <span class="s2">"font-size-adjust"</span><span class="p">,</span>
        <span class="s2">"font-stretch"</span><span class="p">,</span>
        <span class="s2">"font-effect"</span><span class="p">,</span>
        <span class="s2">"font-emphasize"</span><span class="p">,</span>
        <span class="s2">"font-emphasize-position"</span><span class="p">,</span>
        <span class="s2">"font-emphasize-style"</span><span class="p">,</span>
        <span class="s2">"font-smooth"</span><span class="p">,</span>
        <span class="s2">"line-height"</span><span class="p">,</span>
        <span class="s2">"text-align"</span><span class="p">,</span>
        <span class="s2">"-webkit-text-align-last"</span><span class="p">,</span>
        <span class="s2">"-moz-text-align-last"</span><span class="p">,</span>
        <span class="s2">"-ms-text-align-last"</span><span class="p">,</span>
        <span class="s2">"text-align-last"</span><span class="p">,</span>
        <span class="s2">"vertical-align"</span><span class="p">,</span>
        <span class="s2">"white-space"</span><span class="p">,</span>
        <span class="s2">"text-decoration"</span><span class="p">,</span>
        <span class="s2">"text-emphasis"</span><span class="p">,</span>
        <span class="s2">"text-emphasis-color"</span><span class="p">,</span>
        <span class="s2">"text-emphasis-style"</span><span class="p">,</span>
        <span class="s2">"text-emphasis-position"</span><span class="p">,</span>
        <span class="s2">"text-indent"</span><span class="p">,</span>
        <span class="s2">"-ms-text-justify"</span><span class="p">,</span>
        <span class="s2">"text-justify"</span><span class="p">,</span>
        <span class="s2">"letter-spacing"</span><span class="p">,</span>
        <span class="s2">"word-spacing"</span><span class="p">,</span>
        <span class="s2">"-ms-writing-mode"</span><span class="p">,</span>
        <span class="s2">"text-outline"</span><span class="p">,</span>
        <span class="s2">"text-transform"</span><span class="p">,</span>
        <span class="s2">"text-wrap"</span><span class="p">,</span>
        <span class="s2">"-ms-text-overflow"</span><span class="p">,</span>
        <span class="s2">"text-overflow"</span><span class="p">,</span>
        <span class="s2">"text-overflow-ellipsis"</span><span class="p">,</span>
        <span class="s2">"text-overflow-mode"</span><span class="p">,</span>
        <span class="s2">"-ms-word-wrap"</span><span class="p">,</span>
        <span class="s2">"word-wrap"</span><span class="p">,</span>
        <span class="s2">"-ms-word-break"</span><span class="p">,</span>
        <span class="s2">"word-break"</span>
    <span class="p">],</span>
    <span class="p">[</span>
        <span class="s2">"color"</span><span class="p">,</span>
        <span class="s2">"background"</span><span class="p">,</span>
        <span class="s2">"filter:progid:DXImageTransform.Microsoft.AlphaImageLoader"</span><span class="p">,</span>
        <span class="s2">"background-color"</span><span class="p">,</span>
        <span class="s2">"background-image"</span><span class="p">,</span>
        <span class="s2">"background-repeat"</span><span class="p">,</span>
        <span class="s2">"background-attachment"</span><span class="p">,</span>
        <span class="s2">"background-position"</span><span class="p">,</span>
        <span class="s2">"-ms-background-position-x"</span><span class="p">,</span>
        <span class="s2">"background-position-x"</span><span class="p">,</span>
        <span class="s2">"-ms-background-position-y"</span><span class="p">,</span>
        <span class="s2">"background-position-y"</span><span class="p">,</span>
        <span class="s2">"-webkit-background-clip"</span><span class="p">,</span>
        <span class="s2">"-moz-background-clip"</span><span class="p">,</span>
        <span class="s2">"background-clip"</span><span class="p">,</span>
        <span class="s2">"background-origin"</span><span class="p">,</span>
        <span class="s2">"-webkit-background-size"</span><span class="p">,</span>
        <span class="s2">"-moz-background-size"</span><span class="p">,</span>
        <span class="s2">"-o-background-size"</span><span class="p">,</span>
        <span class="s2">"background-size"</span>
    <span class="p">],</span>
    <span class="p">[</span>
        <span class="s2">"outline"</span><span class="p">,</span>
        <span class="s2">"outline-width"</span><span class="p">,</span>
        <span class="s2">"outline-style"</span><span class="p">,</span>
        <span class="s2">"outline-color"</span><span class="p">,</span>
        <span class="s2">"outline-offset"</span><span class="p">,</span>
        <span class="s2">"opacity"</span><span class="p">,</span>
        <span class="s2">"filter:progid:DXImageTransform.Microsoft.Alpha(Opacity"</span><span class="p">,</span>
        <span class="s2">"-ms-filter:\\'progid:DXImageTransform.Microsoft.Alpha"</span><span class="p">,</span>
        <span class="s2">"-ms-interpolation-mode"</span><span class="p">,</span>
        <span class="s2">"-webkit-box-shadow"</span><span class="p">,</span>
        <span class="s2">"-moz-box-shadow"</span><span class="p">,</span>
        <span class="s2">"box-shadow"</span><span class="p">,</span>
        <span class="s2">"filter:progid:DXImageTransform.Microsoft.gradient"</span><span class="p">,</span>
        <span class="s2">"-ms-filter:\\'progid:DXImageTransform.Microsoft.gradient"</span><span class="p">,</span>
        <span class="s2">"text-shadow"</span>
    <span class="p">],</span>
    <span class="p">[</span>
        <span class="s2">"-webkit-transition"</span><span class="p">,</span>
        <span class="s2">"-moz-transition"</span><span class="p">,</span>
        <span class="s2">"-ms-transition"</span><span class="p">,</span>
        <span class="s2">"-o-transition"</span><span class="p">,</span>
        <span class="s2">"transition"</span><span class="p">,</span>
        <span class="s2">"-webkit-transition-delay"</span><span class="p">,</span>
        <span class="s2">"-moz-transition-delay"</span><span class="p">,</span>
        <span class="s2">"-ms-transition-delay"</span><span class="p">,</span>
        <span class="s2">"-o-transition-delay"</span><span class="p">,</span>
        <span class="s2">"transition-delay"</span><span class="p">,</span>
        <span class="s2">"-webkit-transition-timing-function"</span><span class="p">,</span>
        <span class="s2">"-moz-transition-timing-function"</span><span class="p">,</span>
        <span class="s2">"-ms-transition-timing-function"</span><span class="p">,</span>
        <span class="s2">"-o-transition-timing-function"</span><span class="p">,</span>
        <span class="s2">"transition-timing-function"</span><span class="p">,</span>
        <span class="s2">"-webkit-transition-duration"</span><span class="p">,</span>
        <span class="s2">"-moz-transition-duration"</span><span class="p">,</span>
        <span class="s2">"-ms-transition-duration"</span><span class="p">,</span>
        <span class="s2">"-o-transition-duration"</span><span class="p">,</span>
        <span class="s2">"transition-duration"</span><span class="p">,</span>
        <span class="s2">"-webkit-transition-property"</span><span class="p">,</span>
        <span class="s2">"-moz-transition-property"</span><span class="p">,</span>
        <span class="s2">"-ms-transition-property"</span><span class="p">,</span>
        <span class="s2">"-o-transition-property"</span><span class="p">,</span>
        <span class="s2">"transition-property"</span><span class="p">,</span>
        <span class="s2">"-webkit-transform"</span><span class="p">,</span>
        <span class="s2">"-moz-transform"</span><span class="p">,</span>
        <span class="s2">"-ms-transform"</span><span class="p">,</span>
        <span class="s2">"-o-transform"</span><span class="p">,</span>
        <span class="s2">"transform"</span><span class="p">,</span>
        <span class="s2">"-webkit-transform-origin"</span><span class="p">,</span>
        <span class="s2">"-moz-transform-origin"</span><span class="p">,</span>
        <span class="s2">"-ms-transform-origin"</span><span class="p">,</span>
        <span class="s2">"-o-transform-origin"</span><span class="p">,</span>
        <span class="s2">"transform-origin"</span><span class="p">,</span>
        <span class="s2">"-webkit-animation"</span><span class="p">,</span>
        <span class="s2">"-moz-animation"</span><span class="p">,</span>
        <span class="s2">"-ms-animation"</span><span class="p">,</span>
        <span class="s2">"-o-animation"</span><span class="p">,</span>
        <span class="s2">"animation"</span><span class="p">,</span>
        <span class="s2">"-webkit-animation-name"</span><span class="p">,</span>
        <span class="s2">"-moz-animation-name"</span><span class="p">,</span>
        <span class="s2">"-ms-animation-name"</span><span class="p">,</span>
        <span class="s2">"-o-animation-name"</span><span class="p">,</span>
        <span class="s2">"animation-name"</span><span class="p">,</span>
        <span class="s2">"-webkit-animation-duration"</span><span class="p">,</span>
        <span class="s2">"-moz-animation-duration"</span><span class="p">,</span>
        <span class="s2">"-ms-animation-duration"</span><span class="p">,</span>
        <span class="s2">"-o-animation-duration"</span><span class="p">,</span>
        <span class="s2">"animation-duration"</span><span class="p">,</span>
        <span class="s2">"-webkit-animation-play-state"</span><span class="p">,</span>
        <span class="s2">"-moz-animation-play-state"</span><span class="p">,</span>
        <span class="s2">"-ms-animation-play-state"</span><span class="p">,</span>
        <span class="s2">"-o-animation-play-state"</span><span class="p">,</span>
        <span class="s2">"animation-play-state"</span><span class="p">,</span>
        <span class="s2">"-webkit-animation-timing-function"</span><span class="p">,</span>
        <span class="s2">"-moz-animation-timing-function"</span><span class="p">,</span>
        <span class="s2">"-ms-animation-timing-function"</span><span class="p">,</span>
        <span class="s2">"-o-animation-timing-function"</span><span class="p">,</span>
        <span class="s2">"animation-timing-function"</span><span class="p">,</span>
        <span class="s2">"-webkit-animation-delay"</span><span class="p">,</span>
        <span class="s2">"-moz-animation-delay"</span><span class="p">,</span>
        <span class="s2">"-ms-animation-delay"</span><span class="p">,</span>
        <span class="s2">"-o-animation-delay"</span><span class="p">,</span>
        <span class="s2">"animation-delay"</span><span class="p">,</span>
        <span class="s2">"-webkit-animation-iteration-count"</span><span class="p">,</span>
        <span class="s2">"-moz-animation-iteration-count"</span><span class="p">,</span>
        <span class="s2">"-ms-animation-iteration-count"</span><span class="p">,</span>
        <span class="s2">"-o-animation-iteration-count"</span><span class="p">,</span>
        <span class="s2">"animation-iteration-count"</span><span class="p">,</span>
        <span class="s2">"-webkit-animation-direction"</span><span class="p">,</span>
        <span class="s2">"-moz-animation-direction"</span><span class="p">,</span>
        <span class="s2">"-ms-animation-direction"</span><span class="p">,</span>
        <span class="s2">"-o-animation-direction"</span><span class="p">,</span>
        <span class="s2">"animation-direction"</span>
    <span class="p">],</span>
    <span class="p">[</span>
        <span class="s2">"content"</span><span class="p">,</span>
        <span class="s2">"quotes"</span><span class="p">,</span>
        <span class="s2">"counter-reset"</span><span class="p">,</span>
        <span class="s2">"counter-increment"</span><span class="p">,</span>
        <span class="s2">"resize"</span><span class="p">,</span>
        <span class="s2">"cursor"</span><span class="p">,</span>
        <span class="s2">"-webkit-user-select"</span><span class="p">,</span>
        <span class="s2">"-moz-user-select"</span><span class="p">,</span>
        <span class="s2">"-ms-user-select"</span><span class="p">,</span>
        <span class="s2">"user-select"</span><span class="p">,</span>
        <span class="s2">"nav-index"</span><span class="p">,</span>
        <span class="s2">"nav-up"</span><span class="p">,</span>
        <span class="s2">"nav-right"</span><span class="p">,</span>
        <span class="s2">"nav-down"</span><span class="p">,</span>
        <span class="s2">"nav-left"</span><span class="p">,</span>
        <span class="s2">"-moz-tab-size"</span><span class="p">,</span>
        <span class="s2">"-o-tab-size"</span><span class="p">,</span>
        <span class="s2">"tab-size"</span><span class="p">,</span>
        <span class="s2">"-webkit-hyphens"</span><span class="p">,</span>
        <span class="s2">"-moz-hyphens"</span><span class="p">,</span>
        <span class="s2">"hyphens"</span><span class="p">,</span>
        <span class="s2">"pointer-events"</span>
    <span class="p">]</span>
<span class="p">]</span></code></pre></div>
    </div>
</div>

<div class="section" id="css-color">
    <div class="col">
        <h3>颜色</h3>
        <p>颜色16进制用小写字母；</p>
        <p>颜色16进制尽量用简写。</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* not good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="k">color</span><span class="o">:</span> <span class="m">#ABCDEF</span><span class="p">;</span>
    <span class="k">background-color</span><span class="o">:</span> <span class="m">#001122</span><span class="p">;</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="k">color</span><span class="o">:</span> <span class="m">#abcdef</span><span class="p">;</span>
    <span class="k">background-color</span><span class="o">:</span> <span class="m">#012</span><span class="p">;</span>
<span class="p">}</span></code></pre></div>
    </div>
</div>

<div class="section" id="css-shorthand">
    <div class="col">
        <h3>属性简写</h3>
        <p>属性简写需要你非常清楚属性值的正确顺序，而且在大多数情况下并不需要设置属性简写中包含的所有值，所以建议尽量分开声明会更加清晰；</p>
        <p><code>margin</code> 和 <code>padding</code> 相反，需要使用简写；</p>
        <p>常见的属性简写包括：</p>
        <ul>
            <li><code>font</code></li>
            <li><code>background</code></li>
            <li><code>transition</code></li>
            <li><code>animation</code></li>
        </ul>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* not good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="n">transition</span><span class="o">:</span> <span class="k">opacity</span> <span class="m">1s</span> <span class="n">linear</span> <span class="m">2s</span><span class="p">;</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="n">transition</span><span class="o">-</span><span class="n">delay</span><span class="o">:</span> <span class="m">2s</span><span class="p">;</span>
    <span class="n">transition</span><span class="o">-</span><span class="n">timing</span><span class="o">-</span><span class="n">function</span><span class="o">:</span> <span class="n">linear</span><span class="p">;</span>
    <span class="n">transition</span><span class="o">-</span><span class="n">duration</span><span class="o">:</span> <span class="m">1s</span><span class="p">;</span>
    <span class="n">transition</span><span class="o">-</span><span class="n">property</span><span class="o">:</span> <span class="k">opacity</span><span class="p">;</span>
<span class="p">}</span></code></pre></div>
    </div>
</div>

<div class="section" id="css-media-queries">
    <div class="col">
        <h3>媒体查询</h3>
        <p>尽量将媒体查询的规则靠近与他们相关的规则，不要将他们一起放到一个独立的样式文件中，或者丢在文档的最底部，这样做只会让大家以后更容易忘记他们。</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-css" data-lang="css"><span class="nc">.element</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="nc">.element-avatar</span><span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="k">@media</span> <span class="o">(</span><span class="nt">min-width</span><span class="o">:</span> <span class="nt">480px</span><span class="o">)</span> <span class="p">{</span>
    <span class="nc">.element</span> <span class="p">{</span>
        <span class="o">...</span>
    <span class="p">}</span>

    <span class="nc">.element-avatar</span> <span class="p">{</span>
        <span class="o">...</span>
    <span class="p">}</span>
<span class="p">}</span></code></pre></div>
    </div>
</div>

<div class="section" id="css-scss">
    <div class="col">
        <h3>SCSS相关</h3>
        <p>提交的代码中不要有 <code>@debug</code>；</p>
        <div>
            <p>声明顺序：</p>
            <ul>
                <li><code>@extend</code></li>
                <li>不包含 <code>@content</code> 的 <code>@include</code></li>
                <li>包含 <code>@content</code> 的 <code>@include</code></li>
                <li>自身属性</li>
                <li>嵌套规则</li>
            </ul>
        </div>
        <p><code>@import</code> 引入的文件不需要开头的'_'和结尾的'.scss'；</p>
        <p>嵌套最多不能超过5层；</p>
        <p><code>@extend</code> 中使用placeholder选择器；</p>
        <p>去掉不必要的父级引用符号'&amp;'。</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* not good */</span>
<span class="k">@import</span> <span class="s2">"_dialog.scss"</span><span class="p">;</span>

<span class="c">/* good */</span>
<span class="k">@import</span> <span class="s2">"dialog"</span><span class="p">;</span>

<span class="c">/* not good */</span>
<span class="nc">.fatal</span> <span class="p">{</span>
    <span class="o">@</span><span class="n">extend</span> <span class="o">.</span><span class="n">error</span><span class="p">;</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="nc">.fatal</span> <span class="p">{</span>
    <span class="o">@</span><span class="n">extend</span> <span class="o">%</span><span class="n">error</span><span class="p">;</span>
<span class="p">}</span>

<span class="c">/* not good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="o">&amp;</span> <span class="o">&gt;</span> <span class="o">.</span><span class="n">dialog</span> <span class="err">{</span>
        <span class="o">...</span>
    <span class="p">}</span>
<span class="err">}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="o">&gt;</span> <span class="o">.</span><span class="n">dialog</span> <span class="err">{</span>
        <span class="o">...</span>
    <span class="p">}</span>
<span class="err">}</span></code></pre></div>
    </div>
</div>

<div class="section" id="css-miscellaneous">
    <div class="col">
        <h3>杂项</h3>
        <p>不允许有空的规则；</p>
        <p>元素选择器用小写字母；</p>
        <p>去掉小数点前面的0；</p>
        <p>去掉数字中不必要的小数点和末尾的0；</p>
        <p>属性值'0'后面不要加单位；</p>
        <p>同个属性不同前缀的写法需要在垂直方向保持对齐，具体参照右边的写法；</p>
        <p>无前缀的标准属性应该写在有前缀的属性后面；</p>
        <p>不要在同个规则里出现重复的属性，如果重复的属性是连续的则没关系；</p>
        <p>不要在一个文件里出现两个相同的规则；</p>
        <p>用 <code>border: 0;</code> 代替 <code>border: none;</code>；</p>
        <p>选择器不要超过4层（在scss中如果超过4层应该考虑用嵌套的方式来写）；</p>
        <p>发布的代码中不要有 <code>@import</code>；</p>
        <p>尽量少用'*'选择器。</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* not good */</span>
<span class="nc">.element</span> <span class="p">{</span>
<span class="p">}</span>

<span class="c">/* not good */</span>
<span class="nt">LI</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="nt">li</span> <span class="p">{</span>
    <span class="o">...</span>
<span class="p">}</span>

<span class="c">/* not good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="k">color</span><span class="o">:</span> <span class="n">rgba</span><span class="p">(</span><span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="o">.</span><span class="m">5</span><span class="p">);</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="k">color</span><span class="o">:</span> <span class="n">rgba</span><span class="p">(</span><span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="o">,</span> <span class="o">.</span><span class="m">5</span><span class="p">);</span>
<span class="p">}</span>

<span class="c">/* not good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="k">width</span><span class="o">:</span> <span class="m">50.0px</span><span class="p">;</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="k">width</span><span class="o">:</span> <span class="m">50px</span><span class="p">;</span>
<span class="p">}</span>

<span class="c">/* not good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="k">width</span><span class="o">:</span> <span class="m">0px</span><span class="p">;</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="k">width</span><span class="o">:</span> <span class="m">0</span><span class="p">;</span>
<span class="p">}</span>

<span class="c">/* not good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="k">border</span><span class="o">-</span><span class="n">radius</span><span class="o">:</span> <span class="m">3px</span><span class="p">;</span>
    <span class="o">-</span><span class="n">webkit</span><span class="o">-</span><span class="k">border</span><span class="o">-</span><span class="n">radius</span><span class="o">:</span> <span class="m">3px</span><span class="p">;</span>
    <span class="o">-</span><span class="n">moz</span><span class="o">-</span><span class="k">border</span><span class="o">-</span><span class="n">radius</span><span class="o">:</span> <span class="m">3px</span><span class="p">;</span>

    <span class="k">background</span><span class="o">:</span> <span class="n">linear</span><span class="o">-</span><span class="n">gradient</span><span class="p">(</span><span class="n">to</span> <span class="k">bottom</span><span class="o">,</span> <span class="m">#fff</span> <span class="m">0</span><span class="o">,</span> <span class="m">#eee</span> <span class="m">100%</span><span class="p">);</span>
    <span class="k">background</span><span class="o">:</span> <span class="o">-</span><span class="n">webkit</span><span class="o">-</span><span class="n">linear</span><span class="o">-</span><span class="n">gradient</span><span class="p">(</span><span class="k">top</span><span class="o">,</span> <span class="m">#fff</span> <span class="m">0</span><span class="o">,</span> <span class="m">#eee</span> <span class="m">100%</span><span class="p">);</span>
    <span class="k">background</span><span class="o">:</span> <span class="o">-</span><span class="n">moz</span><span class="o">-</span><span class="n">linear</span><span class="o">-</span><span class="n">gradient</span><span class="p">(</span><span class="k">top</span><span class="o">,</span> <span class="m">#fff</span> <span class="m">0</span><span class="o">,</span> <span class="m">#eee</span> <span class="m">100%</span><span class="p">);</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="o">-</span><span class="n">webkit</span><span class="o">-</span><span class="k">border</span><span class="o">-</span><span class="n">radius</span><span class="o">:</span> <span class="m">3px</span><span class="p">;</span>
       <span class="o">-</span><span class="n">moz</span><span class="o">-</span><span class="k">border</span><span class="o">-</span><span class="n">radius</span><span class="o">:</span> <span class="m">3px</span><span class="p">;</span>
            <span class="k">border</span><span class="o">-</span><span class="n">radius</span><span class="o">:</span> <span class="m">3px</span><span class="p">;</span>

    <span class="k">background</span><span class="o">:</span> <span class="o">-</span><span class="n">webkit</span><span class="o">-</span><span class="n">linear</span><span class="o">-</span><span class="n">gradient</span><span class="p">(</span><span class="k">top</span><span class="o">,</span> <span class="m">#fff</span> <span class="m">0</span><span class="o">,</span> <span class="m">#eee</span> <span class="m">100%</span><span class="p">);</span>
    <span class="k">background</span><span class="o">:</span>    <span class="o">-</span><span class="n">moz</span><span class="o">-</span><span class="n">linear</span><span class="o">-</span><span class="n">gradient</span><span class="p">(</span><span class="k">top</span><span class="o">,</span> <span class="m">#fff</span> <span class="m">0</span><span class="o">,</span> <span class="m">#eee</span> <span class="m">100%</span><span class="p">);</span>
    <span class="k">background</span><span class="o">:</span>         <span class="n">linear</span><span class="o">-</span><span class="n">gradient</span><span class="p">(</span><span class="n">to</span> <span class="k">bottom</span><span class="o">,</span> <span class="m">#fff</span> <span class="m">0</span><span class="o">,</span> <span class="m">#eee</span> <span class="m">100%</span><span class="p">);</span>
<span class="p">}</span>

<span class="c">/* not good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="k">color</span><span class="o">:</span> <span class="k">rgb</span><span class="p">(</span><span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="p">);</span>
    <span class="k">width</span><span class="o">:</span> <span class="m">50px</span><span class="p">;</span>
    <span class="k">color</span><span class="o">:</span> <span class="n">rgba</span><span class="p">(</span><span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="o">,</span> <span class="o">.</span><span class="m">5</span><span class="p">);</span>
<span class="p">}</span>

<span class="c">/* good */</span>
<span class="nc">.element</span> <span class="p">{</span>
    <span class="k">color</span><span class="o">:</span> <span class="k">rgb</span><span class="p">(</span><span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="p">);</span>
    <span class="k">color</span><span class="o">:</span> <span class="n">rgba</span><span class="p">(</span><span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="o">,</span> <span class="m">0</span><span class="o">,</span> <span class="o">.</span><span class="m">5</span><span class="p">);</span>
<span class="p">}</span></code></pre></div>
    </div>
</div>

