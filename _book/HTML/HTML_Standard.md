# HTML代码规范

<ul>
            <li><a href="#html-syntax">语法</a></li>
            <li><a href="#html-doctype">HTML5 doctype</a></li>
            <li><a href="#html-lang">lang属性</a></li>
            <li><a href="#html-encoding">字符编码</a></li>
            <li><a href="#html-ie-compatibility-mode">IE兼容模式</a></li>
            <li><a href="#html-style-script">引入CSS, JS</a></li>
            <li><a href="#html-attribute-order">属性顺序</a></li>
            <li><a href="#html-boolean-attributes">boolean属性</a></li>
            <li><a href="#html-javascript">JS生成标签</a></li>
            <li><a href="#html-reducing-markup">减少标签数量</a></li>
            <li><a href="#html-practicality">实用高于完美</a></li>
</ul>

<div class="section" id="html-syntax">
    <div class="col">
        <h3>语法</h3>
        <ul>
            <li>缩进使用soft tab（4个空格）；</li>
            <li>嵌套的节点应该缩进；</li>
            <li>在属性上，使用双引号，不要使用单引号；</li>
            <li>属性名全小写，用中划线做分隔符；</li>
            <li>不要在自动闭合标签结尾处使用斜线；</li>
            <li>不要忽略可选的关闭标签，例：<code>&lt;/li&gt;</code> 和 <code>&lt;/body&gt;</code>。</li>
        </ul>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-html" data-lang="html"><span class="cp">&lt;!DOCTYPE html&gt;</span>
<span class="nt">&lt;html&gt;</span>
    <span class="nt">&lt;head&gt;</span>
        <span class="nt">&lt;title&gt;</span>Page title<span class="nt">&lt;/title&gt;</span>
    <span class="nt">&lt;/head&gt;</span>
    <span class="nt">&lt;body&gt;</span>
        <span class="nt">&lt;img</span> <span class="na">src=</span><span class="s">"images/company_logo.png"</span> <span class="na">alt=</span><span class="s">"Company"</span><span class="nt">&gt;</span>

        <span class="nt">&lt;h1</span> <span class="na">class=</span><span class="s">"hello-world"</span><span class="nt">&gt;</span>Hello, world!<span class="nt">&lt;/h1&gt;</span>
    <span class="nt">&lt;/body&gt;</span>
<span class="nt">&lt;/html&gt;</span></code></pre></div>
    </div>
</div>

<div class="section" id="html-doctype">
    <div class="col">
        <h3>HTML5 doctype</h3>
        <p>在页面开头使用这个简单地doctype来启用标准模式，使其在每个浏览器中尽可能一致的展现；</p>
        <p>虽然doctype不区分大小写，但是按照惯例，doctype大写</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-html" data-lang="html"><span class="cp">&lt;!DOCTYPE html&gt;</span>
<span class="nt">&lt;html&gt;</span>
	...
<span class="nt">&lt;/html&gt;</span></code></pre></div>
    </div>
</div>

<div class="section" id="html-lang">
    <div class="col">
        <h3>lang属性</h3>
        <p>根据HTML5规范：</p>
        <blockquote>
            <p>应在html标签上加上lang属性。这会给语音工具和翻译工具帮助，告诉它们应当怎么去发音和翻译。</p>
        </blockquote>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-html" data-lang="html"><span class="cp">&lt;!DOCTYPE html&gt;</span>
<span class="nt">&lt;html</span> <span class="na">lang=</span><span class="s">"en-us"</span><span class="nt">&gt;</span>
    ...
<span class="nt">&lt;/html&gt;</span></code></pre></div>
    </div>
</div>

<div class="section" id="html-encoding">
    <div class="col">
        <h3>字符编码</h3>
        <p>通过声明一个明确的字符编码，让浏览器轻松、快速的确定适合网页内容的渲染方式，通常指定为'UTF-8'。</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-html" data-lang="html"><span class="cp">&lt;!DOCTYPE html&gt;</span>
<span class="nt">&lt;html&gt;</span>
    <span class="nt">&lt;head&gt;</span>
        <span class="nt">&lt;meta</span> <span class="na">charset=</span><span class="s">"UTF-8"</span><span class="nt">&gt;</span>
    <span class="nt">&lt;/head&gt;</span>
    ...
<span class="nt">&lt;/html&gt;</span></code></pre></div>
    </div>
</div>

<div class="section" id="html-ie-compatibility-mode">
    <div class="col">
        <h3>IE兼容模式</h3>
        <p>用 <code>&lt;meta&gt;</code> 标签可以指定页面应该用什么版本的IE来渲染；</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-html" data-lang="html"><span class="cp">&lt;!DOCTYPE html&gt;</span>
<span class="nt">&lt;html&gt;</span>
    <span class="nt">&lt;head&gt;</span>
        <span class="nt">&lt;meta</span> <span class="na">http-equiv=</span><span class="s">"X-UA-Compatible"</span> <span class="na">content=</span><span class="s">"IE=Edge"</span><span class="nt">&gt;</span>
    <span class="nt">&lt;/head&gt;</span>
    ...
<span class="nt">&lt;/html&gt;</span></code></pre></div>
    </div>
</div>

<div class="section" id="html-style-script">
    <div class="col">
        <h3>引入CSS, JS</h3>
        <p>根据HTML5规范, 通常在引入CSS和JS时不需要指明 <code>type</code>，因为 <code>text/css</code> 和 <code>text/javascript</code> 分别是他们的默认值。</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-html" data-lang="html"><span class="c">&lt;!-- External CSS --&gt;</span>
<span class="nt">&lt;link</span> <span class="na">rel=</span><span class="s">"stylesheet"</span> <span class="na">href=</span><span class="s">"code_guide.css"</span><span class="nt">&gt;</span>

<span class="c">&lt;!-- In-document CSS --&gt;</span>
<span class="nt">&lt;style&gt;</span>
    <span class="o">...</span>
<span class="nt">&lt;/style&gt;</span>

<span class="c">&lt;!-- External JS --&gt;</span>
<span class="nt">&lt;script </span><span class="na">src=</span><span class="s">"code_guide.js"</span><span class="nt">&gt;&lt;/script&gt;</span>

<span class="c">&lt;!-- In-document JS --&gt;</span>
<span class="nt">&lt;script&gt;</span>
    <span class="p">...</span>
<span class="nt">&lt;/script&gt;</span></code></pre></div>
    </div>
</div>

<div class="section" id="html-attribute-order">
    <div class="col">
        <h3>属性顺序</h3>
        <p>属性应该按照特定的顺序出现以保证易读性；</p>
        <ul>
            <li><code>class</code></li>
            <li><code>id</code></li>
            <li><code>name</code></li>
            <li><code>data-*</code></li>
            <li><code>src</code>, <code>for</code>, <code>type</code>, <code>href</code>, <code>value</code> , <code>max-length</code>, <code>max</code>, <code>min</code>, <code>pattern</code></li>
            <li><code>placeholder</code>, <code>title</code>, <code>alt</code></li>
            <li><code>aria-*</code>, <code>role</code></li>
            <li><code>required</code>, <code>readonly</code>, <code>disabled</code></li>
        </ul>
        <p>class是为高可复用组件设计的，所以应处在第一位；</p>
        <p>id更加具体且应该尽量少使用，所以将它放在第二位。</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-html" data-lang="html"><span class="nt">&lt;a</span> <span class="na">class=</span><span class="s">"..."</span> <span class="na">id=</span><span class="s">"..."</span> <span class="na">data-modal=</span><span class="s">"toggle"</span> <span class="na">href=</span><span class="s">"#"</span><span class="nt">&gt;</span>Example link<span class="nt">&lt;/a&gt;</span>

<span class="nt">&lt;input</span> <span class="na">class=</span><span class="s">"form-control"</span> <span class="na">type=</span><span class="s">"text"</span><span class="nt">&gt;</span>

<span class="nt">&lt;img</span> <span class="na">src=</span><span class="s">"..."</span> <span class="na">alt=</span><span class="s">"..."</span><span class="nt">&gt;</span></code></pre></div>
    </div>
</div>

<div class="section" id="html-boolean-attributes">
    <div class="col">
        <h3>boolean属性</h3>
        <p>boolean属性指不需要声明取值的属性，XHTML需要每个属性声明取值，但是HTML5并不需要；</p>
        <blockquote>
            <p>boolean属性的存在表示取值为true，不存在则表示取值为false。</p>
        </blockquote>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-html" data-lang="html"><span class="nt">&lt;input</span> <span class="na">type=</span><span class="s">"text"</span> <span class="na">disabled</span><span class="nt">&gt;</span>

<span class="nt">&lt;input</span> <span class="na">type=</span><span class="s">"checkbox"</span> <span class="na">value=</span><span class="s">"1"</span> <span class="na">checked</span><span class="nt">&gt;</span>

<span class="nt">&lt;select&gt;</span>
    <span class="nt">&lt;option</span> <span class="na">value=</span><span class="s">"1"</span> <span class="na">selected</span><span class="nt">&gt;</span>1<span class="nt">&lt;/option&gt;</span>
<span class="nt">&lt;/select&gt;</span></code></pre></div>
    </div>
</div>

<div class="section" id="html-javascript">
    <div class="col">
        <h3>JS生成标签</h3>
        <p>在JS文件中生成标签让内容变得更难查找，更难编辑，性能更差。应该尽量避免这种情况的出现。</p>
    </div>
</div>

<div class="section" id="html-reducing-markup">
    <div class="col">
        <h3>减少标签数量</h3>
        <p>在编写HTML代码时，需要尽量避免多余的父节点；</p>
        <p>很多时候，需要通过迭代和重构来使HTML变得更少。</p>
    </div>
    <div class="col">
        <div class="highlight"><pre><code class="language-html" data-lang="html"><span class="c">&lt;!-- Not well --&gt;</span>
<span class="nt">&lt;span</span> <span class="na">class=</span><span class="s">"avatar"</span><span class="nt">&gt;</span>
    <span class="nt">&lt;img</span> <span class="na">src=</span><span class="s">"..."</span><span class="nt">&gt;</span>
<span class="nt">&lt;/span&gt;</span>

<span class="c">&lt;!-- Better --&gt;</span>
<span class="nt">&lt;img</span> <span class="na">class=</span><span class="s">"avatar"</span> <span class="na">src=</span><span class="s">"..."</span><span class="nt">&gt;</span></code></pre></div>
    </div>
</div>

<div class="section" id="html-practicality">
    <div class="col">
        <h3>实用高于完美</h3>
        <p>尽量遵循HTML标准和语义，但是不应该以浪费实用性作为代价；</p>
        <p>任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。</p>
    </div>
</div>
