# 第一节 书写规范
<ol>
<li><a style="font-size:24px;" href="#suojin">缩进</a></li>
<li><a style="font-size:24px;" href="#danhang">单行长度</a></li>
<li><a style="font-size:24px;" href="#fenhao">分号</a></li>
<li><a style="font-size:24px;" href="#kongge">空格</a></li>
<li><a style="font-size:24px;" href="#huanhang">空行</a></li>
<li><a style="font-size:24px;" href="#danhangzhushi">单行注释</a></li>
<li><a style="font-size:24px;" href="#duohangzhushi">多行注释</a></li>
<li><a style="font-size:24px;" href="#wendangzhushi">文档注释</a></li>
<li><a style="font-size:24px;" href="#yinhao">引号</a></li>
<li><a style="font-size:24px;" href="#bianliangmingming">变量命名</a></li>
<li><a style="font-size:24px;" href="#bianliangshengming">变量声明</a></li>
<li><a style="font-size:24px;" href="#hanshu">函数</a></li>
<li><a style="font-size:24px;" href="#shuzu">数组、对象</a></li>
<li><a style="font-size:24px;" href="#null">null</a></li>
<li><a style="font-size:24px;" href="#undefined">undefined</a></li>
<li><a style="font-size:24px;" href="#zaxiang">杂项</a></li>
</ol>

<div class="section" id="suojin">
    <div class="col">
        <h3>缩进</h3>
        <p>使用soft tab（4个空格）。</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-javascript" data-lang="javascript"><span class="kd">var</span> <span class="nx">x</span> <span class="o">=</span> <span class="mi">1</span><span class="p">,</span>
    <span class="nx">y</span> <span class="o">=</span> <span class="mi">1</span><span class="p">;</span>

<span class="k">if</span> <span class="p">(</span><span class="nx">x</span> <span class="o">&lt;</span> <span class="nx">y</span><span class="p">)</span> <span class="p">{</span>
    <span class="nx">x</span> <span class="o">+=</span> <span class="mi">10</span><span class="p">;</span>
<span class="p">}</span> <span class="k">else</span> <span class="p">{</span>
    <span class="nx">x</span> <span class="o">+=</span> <span class="mi">1</span><span class="p">;</span>
<span class="p">}</span></code></pre></div>
    </div>
</div>

<div class="section" id="danhang">
    <div class="col">
        <h3>单行长度</h3>
        <p>不要超过80，但如果编辑器开启word wrap可以不考虑单行长度。</p>
    </div>
</div>

<div class="section" id="fenhao">
    <div class="col">
        <h3>分号</h3>
        <p>以下几种情况后需加分号：</p>
        <ul>
            <li>变量声明</li>
            <li>表达式</li>
            <li>return</li>
            <li>throw</li>
            <li>break</li>
            <li>continue</li>
            <li>do-while</li>
        </ul>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-javascript" data-lang="javascript"><span class="cm">/* var declaration */</span>
<span class="kd">var</span> <span class="nx">x</span> <span class="o">=</span> <span class="mi">1</span><span class="p">;</span>

<span class="cm">/* expression statement */</span>
<span class="nx">x</span><span class="o">++</span><span class="p">;</span>

<span class="cm">/* do-while */</span>
<span class="k">do</span> <span class="p">{</span>
    <span class="nx">x</span><span class="o">++</span><span class="p">;</span>
<span class="p">}</span> <span class="k">while</span> <span class="p">(</span><span class="nx">x</span> <span class="o">&lt;</span> <span class="mi">10</span><span class="p">);</span></code></pre></div>
    </div>
</div>

<div class="section" id="kongge">
    <div class="col">
        <h3>空格</h3>
        <p>以下几种情况不需要空格：</p>
        <ul>
            <li>对象的属性名后</li>
            <li>前缀一元运算符后</li>
            <li>后缀一元运算符前</li>
            <li>函数调用括号前</li>
            <li>无论是函数声明还是函数表达式，'('前不要空格</li>
            <li>数组的'['后和']'前</li>
            <li>对象的'{'后和'}'前</li>
            <li>运算符'('后和')'前</li>
        </ul>
        <p>以下几种情况需要空格：</p>
        <ul>
            <li>二元运算符前后</li>
            <li>三元运算符'?:'前后</li>
            <li>代码块'{'前</li>
            <li>下列关键字前：<code>else</code>, <code>while</code>, <code>catch</code>, <code>finally</code></li>
            <li>下列关键字后：<code>if</code>, <code>else</code>, <code>for</code>, <code>while</code>, <code>do</code>, <code>switch</code>, <code>case</code>, <code>try</code>, <code>catch</code>, <code>finally</code>, <code>with</code>, <code>return</code>, <code>typeof</code></li>
            <li>单行注释'//'后（若单行注释和代码同行，则'//'前也需要），多行注释'*'后</li>
            <li>对象的属性值前</li>
            <li>for循环，分号后留有一个空格，前置条件如果有多个，逗号后留一个空格</li>
            <li>无论是函数声明还是函数表达式，'{'前一定要有空格</li>
            <li>函数的参数之间</li>
        </ul>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-javascript" data-lang="javascript"><span class="c1">// not good</span>
<span class="kd">var</span> <span class="nx">a</span> <span class="o">=</span> <span class="p">{</span>
    <span class="nx">b</span> <span class="o">:</span><span class="mi">1</span>
<span class="p">};</span>

<span class="c1">// good</span>
<span class="kd">var</span> <span class="nx">a</span> <span class="o">=</span> <span class="p">{</span>
    <span class="nx">b</span><span class="o">:</span> <span class="mi">1</span>
<span class="p">};</span>

<span class="c1">// not good</span>
<span class="o">++</span> <span class="nx">x</span><span class="p">;</span>
<span class="nx">y</span> <span class="o">++</span><span class="p">;</span>
<span class="nx">z</span> <span class="o">=</span> <span class="nx">x</span><span class="o">?</span><span class="mi">1</span><span class="o">:</span><span class="mi">2</span><span class="p">;</span>

<span class="c1">// good</span>
<span class="o">++</span><span class="nx">x</span><span class="p">;</span>
<span class="nx">y</span><span class="o">++</span><span class="p">;</span>
<span class="nx">z</span> <span class="o">=</span> <span class="nx">x</span> <span class="o">?</span> <span class="mi">1</span> <span class="o">:</span> <span class="mi">2</span><span class="p">;</span>

<span class="c1">// not good</span>
<span class="kd">var</span> <span class="nx">a</span> <span class="o">=</span> <span class="p">[</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">2</span> <span class="p">];</span>

<span class="c1">// good</span>
<span class="kd">var</span> <span class="nx">a</span> <span class="o">=</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">];</span>

<span class="c1">// not good</span>
<span class="kd">var</span> <span class="nx">a</span> <span class="o">=</span> <span class="p">(</span> <span class="mi">1</span><span class="o">+</span><span class="mi">2</span> <span class="p">)</span><span class="o">*</span><span class="mi">3</span><span class="p">;</span>

<span class="c1">// good</span>
<span class="kd">var</span> <span class="nx">a</span> <span class="o">=</span> <span class="p">(</span><span class="mi">1</span> <span class="o">+</span> <span class="mi">2</span><span class="p">)</span> <span class="o">*</span> <span class="mi">3</span><span class="p">;</span>

<span class="c1">// no space before '(', one space before '{', one space between function parameters</span>
<span class="kd">var</span> <span class="nx">doSomething</span> <span class="o">=</span> <span class="kd">function</span><span class="p">(</span><span class="nx">a</span><span class="p">,</span> <span class="nx">b</span><span class="p">,</span> <span class="nx">c</span><span class="p">)</span> <span class="p">{</span>
    <span class="c1">// do something</span>
<span class="p">};</span>

<span class="c1">// no space before '('</span>
<span class="nx">doSomething</span><span class="p">(</span><span class="nx">item</span><span class="p">);</span>

<span class="c1">// not good</span>
<span class="k">for</span><span class="p">(</span><span class="nx">i</span><span class="o">=</span><span class="mi">0</span><span class="p">;</span><span class="nx">i</span><span class="o">&lt;</span><span class="mi">6</span><span class="p">;</span><span class="nx">i</span><span class="o">++</span><span class="p">){</span>
    <span class="nx">x</span><span class="o">++</span><span class="p">;</span>
<span class="p">}</span>

<span class="c1">// good</span>
<span class="k">for</span> <span class="p">(</span><span class="nx">i</span> <span class="o">=</span> <span class="mi">0</span><span class="p">;</span> <span class="nx">i</span> <span class="o">&lt;</span> <span class="mi">6</span><span class="p">;</span> <span class="nx">i</span><span class="o">++</span><span class="p">)</span> <span class="p">{</span>
    <span class="nx">x</span><span class="o">++</span><span class="p">;</span>
<span class="p">}</span></code></pre></div>
    </div>
</div>



<div class="section" id="huanhang">
    <div class="col">
        <h3>空行</h3>
        <p>以下几种情况需要空行：</p>
        <ul>
            <li>变量声明后（当变量声明在代码块的最后一行时，则无需空行）</li>
            <li>注释前（当注释在代码块的第一行时，则无需空行）</li>
            <li>代码块后（在函数调用、数组、对象中则无需空行）</li>
            <li>文件最后保留一个空行</li>
        </ul>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-javascript" data-lang="javascript"><span class="c1">// need blank line after variable declaration</span>
<span class="kd">var</span> <span class="nx">x</span> <span class="o">=</span> <span class="mi">1</span><span class="p">;</span>

<span class="c1">// not need blank line when variable declaration is last expression in the current block</span>
<span class="k">if</span> <span class="p">(</span><span class="nx">x</span> <span class="o">&gt;=</span> <span class="mi">1</span><span class="p">)</span> <span class="p">{</span>
    <span class="kd">var</span> <span class="nx">y</span> <span class="o">=</span> <span class="nx">x</span> <span class="o">+</span> <span class="mi">1</span><span class="p">;</span>
<span class="p">}</span>

<span class="kd">var</span> <span class="nx">a</span> <span class="o">=</span> <span class="mi">2</span><span class="p">;</span>

<span class="c1">// need blank line before line comment</span>
<span class="nx">a</span><span class="o">++</span><span class="p">;</span>

<span class="kd">function</span> <span class="nx">b</span><span class="p">()</span> <span class="p">{</span>
    <span class="c1">// not need blank line when comment is first line of block</span>
    <span class="k">return</span> <span class="nx">a</span><span class="p">;</span>
<span class="p">}</span>

<span class="c1">// need blank line after blocks</span>
<span class="k">for</span> <span class="p">(</span><span class="kd">var</span> <span class="nx">i</span> <span class="o">=</span> <span class="mi">0</span><span class="p">;</span> <span class="nx">i</span> <span class="o">&lt;</span> <span class="mi">2</span><span class="p">;</span> <span class="nx">i</span><span class="o">++</span><span class="p">)</span> <span class="p">{</span>
    <span class="k">if</span> <span class="p">(</span><span class="kc">true</span><span class="p">)</span> <span class="p">{</span>
        <span class="k">return</span> <span class="kc">false</span><span class="p">;</span>
    <span class="p">}</span>

    <span class="k">continue</span><span class="p">;</span>
<span class="p">}</span>

<span class="kd">var</span> <span class="nx">obj</span> <span class="o">=</span> <span class="p">{</span>
    <span class="nx">foo</span><span class="o">:</span> <span class="kd">function</span><span class="p">()</span> <span class="p">{</span>
        <span class="k">return</span> <span class="mi">1</span><span class="p">;</span>
    <span class="p">},</span>

    <span class="nx">bar</span><span class="o">:</span> <span class="kd">function</span><span class="p">()</span> <span class="p">{</span>
        <span class="k">return</span> <span class="mi">2</span><span class="p">;</span>
    <span class="p">}</span>
<span class="p">};</span>

<span class="c1">// not need blank line when in argument list, array, object</span>
<span class="nx">func</span><span class="p">(</span>
    <span class="mi">2</span><span class="p">,</span>
    <span class="kd">function</span><span class="p">()</span> <span class="p">{</span>
        <span class="nx">a</span><span class="o">++</span><span class="p">;</span>
    <span class="p">},</span>
    <span class="mi">3</span>
<span class="p">);</span>

<span class="kd">var</span> <span class="nx">foo</span> <span class="o">=</span> <span class="p">[</span>
    <span class="mi">2</span><span class="p">,</span>
    <span class="kd">function</span><span class="p">()</span> <span class="p">{</span>
        <span class="nx">a</span><span class="o">++</span><span class="p">;</span>
    <span class="p">},</span>
    <span class="mi">3</span>
<span class="p">];</span>


<span class="kd">var</span> <span class="nx">foo</span> <span class="o">=</span> <span class="p">{</span>
    <span class="nx">a</span><span class="o">:</span> <span class="mi">2</span><span class="p">,</span>
    <span class="nx">b</span><span class="o">:</span> <span class="kd">function</span><span class="p">()</span> <span class="p">{</span>
        <span class="nx">a</span><span class="o">++</span><span class="p">;</span>
    <span class="p">},</span>
    <span class="nx">c</span><span class="o">:</span> <span class="mi">3</span>
<span class="p">};</span></code></pre></div>
    </div>
</div>




<div class="section" id="js-new-line">
    <div class="col">
        <h3>换行</h3>
        <p>换行的地方，行末必须有','或者运算符；</p>
        <p>以下几种情况不需要换行：</p>
        <ul>
            <li>下列关键字后：<code>else</code>, <code>catch</code>, <code>finally</code></li>
            <li>代码块'{'前</li>
        </ul>
        <p>以下几种情况需要换行：</p>
        <ul>
            <li>代码块'{'后和'}'前</li>
            <li>变量赋值后</li>
        </ul>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-javascript" data-lang="javascript"><span class="c1">// not good</span>
<span class="kd">var</span> <span class="nx">a</span> <span class="o">=</span> <span class="p">{</span>
    <span class="nx">b</span><span class="o">:</span> <span class="mi">1</span>
    <span class="p">,</span> <span class="nx">c</span><span class="o">:</span> <span class="mi">2</span>
<span class="p">};</span>

<span class="nx">x</span> <span class="o">=</span> <span class="nx">y</span>
    <span class="o">?</span> <span class="mi">1</span> <span class="o">:</span> <span class="mi">2</span><span class="p">;</span>

<span class="c1">// good</span>
<span class="kd">var</span> <span class="nx">a</span> <span class="o">=</span> <span class="p">{</span>
    <span class="nx">b</span><span class="o">:</span> <span class="mi">1</span><span class="p">,</span>
    <span class="nx">c</span><span class="o">:</span> <span class="mi">2</span>
<span class="p">};</span>

<span class="nx">x</span> <span class="o">=</span> <span class="nx">y</span> <span class="o">?</span> <span class="mi">1</span> <span class="o">:</span> <span class="mi">2</span><span class="p">;</span>
<span class="nx">x</span> <span class="o">=</span> <span class="nx">y</span> <span class="o">?</span>
    <span class="mi">1</span> <span class="o">:</span> <span class="mi">2</span><span class="p">;</span>

<span class="c1">// no need line break with 'else', 'catch', 'finally'</span>
<span class="k">if</span> <span class="p">(</span><span class="nx">condition</span><span class="p">)</span> <span class="p">{</span>
    <span class="p">...</span>
<span class="p">}</span> <span class="k">else</span> <span class="p">{</span>
    <span class="p">...</span>
<span class="p">}</span>

<span class="k">try</span> <span class="p">{</span>
    <span class="p">...</span>
<span class="p">}</span> <span class="k">catch</span> <span class="p">(</span><span class="nx">e</span><span class="p">)</span> <span class="p">{</span>
    <span class="p">...</span>
<span class="p">}</span> <span class="k">finally</span> <span class="p">{</span>
    <span class="p">...</span>
<span class="p">}</span>

<span class="c1">// not good</span>
<span class="kd">function</span> <span class="nx">test</span><span class="p">()</span>
<span class="p">{</span>
    <span class="p">...</span>
<span class="p">}</span>

<span class="c1">// good</span>
<span class="kd">function</span> <span class="nx">test</span><span class="p">()</span> <span class="p">{</span>
    <span class="p">...</span>
<span class="p">}</span>

<span class="c1">// not good</span>
<span class="kd">var</span> <span class="nx">a</span><span class="p">,</span> <span class="nx">foo</span> <span class="o">=</span> <span class="mi">7</span><span class="p">,</span> <span class="nx">b</span><span class="p">,</span>
    <span class="nx">c</span><span class="p">,</span> <span class="nx">bar</span> <span class="o">=</span> <span class="mi">8</span><span class="p">;</span>

<span class="c1">// good</span>
<span class="kd">var</span> <span class="nx">a</span><span class="p">,</span>
    <span class="nx">foo</span> <span class="o">=</span> <span class="mi">7</span><span class="p">,</span>
    <span class="nx">b</span><span class="p">,</span> <span class="nx">c</span><span class="p">,</span> <span class="nx">bar</span> <span class="o">=</span> <span class="mi">8</span><span class="p">;</span></code></pre></div>
    </div>
</div>

<div class="section" id="danhangzhushi">
    <div class="col">
        <h3>单行注释</h3>
        <p>双斜线后，必须跟一个空格；</p>
        <p>缩进与下一行代码保持一致；</p>
        <p>可位于一个代码行的末尾，与代码间隔一个空格。
    </p></div>
    <div class="col">
        <div class="highlight"><pre><code class="language-javascript" data-lang="javascript"><span class="k">if</span> <span class="p">(</span><span class="nx">condition</span><span class="p">)</span> <span class="p">{</span>
    <span class="c1">// if you made it here, then all security checks passed</span>
    <span class="nx">allowed</span><span class="p">();</span>
<span class="p">}</span>

<span class="kd">var</span> <span class="nx">zhangsan</span> <span class="o">=</span> <span class="s1">'zhangsan'</span><span class="p">;</span> <span class="c1">// one space after code</span></code></pre></div>
    </div>
</div>

<div class="section" id="duohangzhushi">
    <div class="col">
        <h3>多行注释</h3>
        <p>最少三行, '*'后跟一个空格，具体参照右边的写法；</p>
        <p>建议在以下情况下使用：
        </p><ul>
            <li>难于理解的代码段</li>
            <li>可能存在错误的代码段</li>
            <li>浏览器特殊的HACK代码</li>
            <li>业务逻辑强相关的代码</li>
        </ul>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-javascript" data-lang="javascript"><span class="cm">/*</span>
<span class="cm"> * one space after '*'</span>
<span class="cm"> */</span>
<span class="kd">var</span> <span class="nx">x</span> <span class="o">=</span> <span class="mi">1</span><span class="p">;</span></code></pre></div>
    </div>
</div>



<div class="section" id="wendangzhushi">
    <div class="col">
        <h3>文档注释</h3>
        <p>各类标签@param, @method等请参考<a href="http://usejsdoc.org/" target="_blank">usejsdoc</a>和<a href="http://yuri4ever.github.io/jsdoc/" target="_blank">JSDoc Guide</a>；</p>
        <p>建议在以下情况下使用：</p>
        <ul>
            <li>所有常量</li>
            <li>所有函数</li>
            <li>所有类</li>
        </ul>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-javascript" data-lang="javascript"><span class="cm">/**</span>
<span class="cm"> * @func</span>
<span class="cm"> * @desc 一个带参数的函数</span>
<span class="cm"> * @param {string} a - 参数a</span>
<span class="cm"> * @param {number} b=1 - 参数b默认值为1</span>
<span class="cm"> * @param {string} c=1 - 参数c有两种支持的取值&lt;/br&gt;1—表示x&lt;/br&gt;2—表示xx</span>
<span class="cm"> * @param {object} d - 参数d为一个对象</span>
<span class="cm"> * @param {string} d.e - 参数d的e属性</span>
<span class="cm"> * @param {string} d.f - 参数d的f属性</span>
<span class="cm"> * @param {object[]} g - 参数g为一个对象数组</span>
<span class="cm"> * @param {string} g.h - 参数g数组中一项的h属性</span>
<span class="cm"> * @param {string} g.i - 参数g数组中一项的i属性</span>
<span class="cm"> * @param {string} [j] - 参数j是一个可选参数</span>
<span class="cm"> */</span>
<span class="kd">function</span> <span class="nx">foo</span><span class="p">(</span><span class="nx">a</span><span class="p">,</span> <span class="nx">b</span><span class="p">,</span> <span class="nx">c</span><span class="p">,</span> <span class="nx">d</span><span class="p">,</span> <span class="nx">g</span><span class="p">,</span> <span class="nx">j</span><span class="p">)</span> <span class="p">{</span>
    <span class="p">...</span>
<span class="p">}</span></code></pre></div>
    </div>
</div>



<div id="undefined" style ='border-bottom: 1px solid #dfe1e8;Float:left '>  
    <div class="col">
        <h3>undefined</h3>
        <p>永远不要直接使用undefined进行变量判断；</p>
        <p>使用typeof和字符串'undefined'对变量进行判断。</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-javascript" data-lang="javascript"><span class="c1">// not good</span>
        <span class="k">if</span> <span class="p">(</span><span class="nx">person</span> <span class="o">===</span> <span class="kc">undefined</span><span class="p">)</span> <span class="p">{</span>
        <span class="p">...</span>
        <span class="p">}</span>

<span class="c1">// good</span>
<span class="k">if</span> <span class="p">(</span><span class="k">typeof</span> <span class="nx">person</span> <span class="o">===</span> <span class="s1">'undefined'</span><span class="p">)</span> <span class="p">{</span>
    <span class="p">...</span>
<span class="p">}</span></code></pre></div>
    </div>
    </div>

<div id="zaxiang" style ='border-bottom: 1px solid #dfe1e8;Float:left '>      
    <div class="col">
        <h3>杂项</h3>
        <p>不要混用tab和space；</p>
        <p>不要在一处使用多个tab或space；</p>
        <p>换行符统一用'LF'；</p>
        <p>对上下文this的引用只能使用'_this', 'that', 'self'其中一个来命名；</p>
        <p>行尾不要有空白字符；</p>
        <p>switch的falling through和no default的情况一定要有注释特别说明；</p>
        <p>不允许有空的代码块。</p>
    </div>
    <div class="highlight">
        <pre><code class="language-javascript" data-lang="javascript"><span class="c1">// not good</span>
        <span class="kd">var</span> <span class="nx">a</span>   <span class="o">=</span> <span class="mi">1</span><span class="p">;</span>
        <span class="kd">function</span> <span class="nx">Person</span><span class="p">()</span> <span class="p">{</span>
        <span class="c1">// not good</span>
        <span class="kd">var</span> <span class="nx">me</span> <span class="o">=</span> <span class="k">this</span><span class="p">;</span>
        <span class="c1">// good</span>
        <span class="kd">var</span> <span class="nx">_this</span> <span class="o">=</span> <span class="k">this</span><span class="p">;</span>
        <span class="c1">// good</span>
        <span class="kd">var</span> <span class="nx">that</span> <span class="o">=</span> <span class="k">this</span><span class="p">;</span>
        <span class="c1">// good</span>
        <span class="kd">var</span> <span class="nx">self</span> <span class="o">=</span> <span class="k">this</span><span class="p">;</span>
        <span class="p">}</span>
        <span class="c1">// good</span>
        <span class="k">switch</span> <span class="p">(</span><span class="nx">condition</span><span class="p">)</span> <span class="p">{</span>
        <span class="k">case</span> <span class="mi">1</span><span class="o">:</span>
        <span class="k">case</span> <span class="mi">2</span><span class="o">:</span>
        <span class="p">...</span>
        <span class="k">break</span><span class="p">;</span>
        <span class="k">case</span> <span class="mi">3</span><span class="o">:</span>
        <span class="p">...</span>
        <span class="c1">// why fall through</span>
        <span class="k">case</span> <span class="mi">4</span>
        <span class="p">...</span>
        <span class="k">break</span><span class="p">;</span>
        <span class="c1">// why no default</span>
        <span class="p">}</span>

        <span class="c1">// not good with empty block</span>
        <span class="k">if</span> <span class="p">(</span><span class="nx">condition</span><span class="p">)</span> <span class="p">{</span>
        <span class="p">}</span></code></pre>
    </div>
</div>

