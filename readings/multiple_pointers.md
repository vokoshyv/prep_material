A number of problems involving arrays, lists, and strings require us to iterate with more than one pointer. Sometimes pointers may travel at different speeds and may start from a different initial position.

For example, an algorithm that requires one to swap a bunch of values may require multiple pointers.

### Language Specific

*   Languages like Java, C, C++, and Javascript, have `for` loops that are more flexible and can be easily customized to handle two or more pointers. But universally, a `while` loop will give the same flexibility for all languages.
*   Languages like Ruby or Python can use `while` loop to handle looping with multiple pointers.
*   When there are multiple pointers to keep track of, avoid using built in iterators that simply loop from left to right.
*   Lets demonstrate the use of while loops with a few examples.

### Example 1 : Sort a Bit Array

Given a bit array, return it sorted in-place (a bit array is simply an array that contains only bits, either a 1 or a 0).

See if you can solve this in O(N) time and O(1) auxiliary space.

#### Hint 1

Since we want to sort it in-place we should be modifying the values change changing its position rather than creating a new array. Additionally because there are only two possible values, and we know that the 0’s will have to be on the left, and the ones have to be on the right. How can we identify elements to swap?

#### Hint 2

1.  If we have two pointers: one that starts on the very **left**, and one on the very **right**, then we can iterate inward.
2.  We need to iterate the **left** pointer until it hits a 1
3.  Then decrement the **right** pointer to the left until it reaches a 0
4.  Once we find them we will do a swap.

#### Solution

<div>

<pre class="line-numbers"><code class="language-javascript">function bitArraySort(arr) {
    let left = 0;
    let right = arr.length - 1;
    while(left < right) {
      while(arr[left] === 0) { left++; }
      while(arr[right] === 1) { right--; }
      if(left < right) {
         // swap the left and right values
        [arr[left], arr[right]] = [arr[right], arr[left]];
      }
    }
    return arr;
}</code>
	</pre>

</div>

### Challenge 1 : Sorted Two Sum

Given a sorted array of integers and a target value, determine if there exists two integers in the array that sum up to the target value.

See if you can solve this in O(N) time and O(1) auxiliary space.

#### Brute Force

The brute force approach would be, to try out every single possible pair combination and see if the sum matches the target. This would lead to a O(N^2) time complexity because the number of pairs is proportional to N^2.

#### Frequency Hash

We could also try to create a hashtable or map to speed up the search or lookup time to find a match. But this would lead to a O(N) amount of auxiliary space.

#### Hint 1

Given that the array is sorted, we know every element right is equal or larger and every element to the left is lower. How could we approach this in a more efficiently with multiple pointers?

#### Hint 2

1.  If we have two pointers: one that starts on the very **left**, and one on the very **right**, we can find the sum of them.
2.  What happens if this sum is greater? What happens if this sum is less than? And what happens if this sum is equal?
3.  What happens if the two pointers eventually meet and we have not found a pair that matches the target?

### Challenge 2 : Merge Two Sorted Arrays

Given two sorted arrays of integers, combine the values into one sorted array?

**Input:**`[1,3,5], [2,4,6,8,10]`

**Output:** `[1,2,3,4,5,6,8,10]`

See if you can solve this in O(N+M) time and O(N+M) auxiliary space.

#### Brute Force

The brute force approach would be, to concatenate the two arrays into a larger array and perform a sort on the combined array. However the time complexity would be quasilinear O((N+M)log(N+M)) if we used a efficient sorting method such as mergesort.

#### Hint 1

Given that the arrays are sorted, we know the lowest element must either be the first item of array one or the first item of array two.

#### Hint 2

1.  If we have two pointers: one that starts at the beginning of **array1**, and one pointer at the beginning of **array2**, we can place the smaller value into a **results** array.
2.  What happens if the value in **array1** is smaller? What happens if the value in **array2** is smaller? What happens if the values are equal?
3.  What happens if one of the pointers reaches the very end of its array?

<script type="text/javascript">var _self="undefined"!=typeof window?window:"undefined"!=typeof WorkerGlobalScope&&self instanceof WorkerGlobalScope?self:{},Prism=function(){var e=/\blang(?:uage)?-(\w+)\b/i,t=0,n=_self.Prism={util:{encode:function(e){return e instanceof a?new a(e.type,n.util.encode(e.content),e.alias):"Array"===n.util.type(e)?e.map(n.util.encode):e.replace(/&/g,"&").replace(/e.length)break e;if(!(m instanceof a)){u.lastIndex=0;var y=u.exec(m),v=1;if(!y&&h&&p!=r.length-1){var b=r[p+1].matchedStr||r[p+1],k=m+b;if(p<r.length-2&&(k+=r[p+2].matchedstr||r[p+2]),u.lastindex=0,y=u.exec(k),!y)continue;var w="y.index+(g?y[1].length:0);if(w">=m.length)continue;var _=y.index+y[0].length,P=m.length+b.length;if(v=3,P&gt;=_){if(r[p+1].greedy)continue;v=2,k=k.slice(0,P)}m=k}if(y){g&&(f=y[1].length);var w=y.index+f,y=y[0].slice(f),_=w+y.length,S=m.slice(0,w),O=m.slice(_),j=[p,v];S&&j.push(S);var A=new a(i,c?n.tokenize(y,c):y,d,y,h);j.push(A),O&&j.push(O),Array.prototype.splice.apply(r,j)}}}}}return r},hooks:{all:{},add:function(e,t){var a=n.hooks.all;a[e]=a[e]||[],a[e].push(t)},run:function(e,t){var a=n.hooks.all[e];if(a&&a.length)for(var r,l=0;r=a[l++];)r(t)}}},a=n.Token=function(e,t,n,a,r){this.type=e,this.content=t,this.alias=n,this.matchedStr=a||null,this.greedy=!!r};if(a.stringify=function(e,t,r){if("string"==typeof e)return e;if("Array"===n.util.type(e))return e.map(function(n){return a.stringify(n,t,e)}).join("");var l={type:e.type,content:a.stringify(e.content,t,r),tag:"span",classes:["token",e.type],attributes:{},language:t,parent:r};if("comment"==l.type&&(l.attributes.spellcheck="true"),e.alias){var i="Array"===n.util.type(e.alias)?e.alias:[e.alias];Array.prototype.push.apply(l.classes,i)}n.hooks.run("wrap",l);var o="";for(var s in l.attributes)o+=(o?" ":"")+s+'="'+(l.attributes[s]||"")+'"';return"&lt;"+l.tag+' class="'+l.classes.join(" ")+'" '+o+"&gt;"+l.content+"<!--"+l.tag+"-->"},!_self.document)return _self.addEventListener?(_self.addEventListener("message",function(e){var t=JSON.parse(e.data),a=t.language,r=t.code,l=t.immediateClose;_self.postMessage(n.highlight(r,n.languages[a],a)),l&&_self.close()},!1),_self.Prism):_self.Prism;var r=document.currentScript||[].slice.call(document.getElementsByTagName("script")).pop();return r&&(n.filename=r.src,document.addEventListener&&!r.hasAttribute("data-manual")&&document.addEventListener("DOMContentLoaded",n.highlightAll)),_self.Prism}();"undefined"!=typeof module&&module.exports&&(module.exports=Prism),"undefined"!=typeof global&&(global.Prism=Prism); </r.length-2&&(k+=r[p+2].matchedstr||r[p+2]),u.lastindex=0,y=u.exec(k),!y)continue;var></script> <script type="text/javascript">Prism.languages.clike={comment:[{pattern:/(^|[^\\])\/\*[\w\W]*?\*\//,lookbehind:!0},{pattern:/(^|[^\\:])\/\/.*/,lookbehind:!0}],string:{pattern:/(["'])(\\(?:\r\n|[\s\S])|(?!\1)[^\\\r\n])*\1/,greedy:!0},"class-name":{pattern:/((?:\b(?:class|interface|extends|implements|trait|instanceof|new)\s+)|(?:catch\s+\())[a-z0-9_\.\\]+/i,lookbehind:!0,inside:{punctuation:/(\.|\\)/}},keyword:/\b(if|else|while|do|for|return|in|instanceof|function|new|try|throw|catch|finally|null|break|continue)\b/,"boolean":/\b(true|false)\b/,"function":/[a-z0-9_]+(?=\()/i,number:/\b-?(?:0x[\da-f]+|\d*\.?\d+(?:e[+-]?\d+)?)\b/i,operator:/--?|\+\+?|!=?=?|&lt;=?|&gt;=?|==?=?|&&?|\|\|?|\?|\*|\/|~|\^|%/,punctuation:/[{}[\];(),.:]/};</script> <script type="text/javascript">Prism.languages.javascript=Prism.languages.extend("clike",{keyword:/\b(as|async|await|break|case|catch|class|const|continue|debugger|default|delete|do|else|enum|export|extends|finally|for|from|function|get|if|implements|import|in|instanceof|interface|let|new|null|of|package|private|protected|public|return|set|static|super|switch|this|throw|try|typeof|var|void|while|with|yield)\b/,number:/\b-?(0x[\dA-Fa-f]+|0b[01]+|0o[0-7]+|\d*\.?\d+([Ee][+-]?\d+)?|NaN|Infinity)\b/,"function":/[_$a-zA-Z\xA0-\uFFFF][_$a-zA-Z0-9\xA0-\uFFFF]*(?=\()/i}),Prism.languages.insertBefore("javascript","keyword",{regex:{pattern:/(^|[^\/])\/(?!\/)(\[.+?]|\\.|[^\/\\\r\n])+\/[gimyu]{0,5}(?=\s*($|[\r\n,.;})]))/,lookbehind:!0,greedy:!0}}),Prism.languages.insertBefore("javascript","class-name",{"template-string":{pattern:/`(?:\\\\|\\?[^\\])*?`/,greedy:!0,inside:{interpolation:{pattern:/\$\{[^}]+\}/,inside:{"interpolation-punctuation":{pattern:/^\$\{|\}$/,alias:"punctuation"},rest:Prism.languages.javascript}},string:/[\s\S]+/}}}),Prism.languages.markup&&Prism.languages.insertBefore("markup","tag",{script:{pattern:/(<script[\w\w]*?>)[\w\W]*?(?=&lt;\/script&gt;)/i,lookbehind:!0,inside:Prism.languages.javascript,alias:"language-javascript"}}),Prism.languages.js=Prism.languages.javascript; </script[\w\w]*?></script> <script type="text/javascript">!function(){"undefined"!=typeof self&&self.Prism&&self.document&&Prism.hooks.add("complete",function(e){if(e.code){var t=e.element.parentNode,s=/\s*\bline-numbers\b\s*/;if(t&&/pre/i.test(t.nodeName)&&(s.test(t.className)||s.test(e.element.className))&&!e.element.querySelector(".line-numbers-rows")){s.test(e.element.className)&&(e.element.className=e.element.className.replace(s,"")),s.test(t.className)||(t.className+=" line-numbers");var n,a=e.code.match(/\n(?!$)/g),l=a?a.length+1:1,m=new Array(l+1);m=m.join("<span></span>"),n=document.createElement("span"),n.className="line-numbers-rows",n.innerHTML=m,t.hasAttribute("data-start")&&(t.style.counterReset="linenumber "+(parseInt(t.getAttribute("data-start"),10)-1)),e.element.appendChild(n)}}})}();</script>
