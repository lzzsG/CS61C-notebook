---
layout: page
title: About
permalink: /about/
nav_order: 99
---

# 更新历史

<br/><br/>

2024/4/29 first commit

---

# markdown and highlight test

以下是markdown与highlight测试

<br/>

首先是一个可以收起的目录

```jsx
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>
```

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

---

This is the base Jekyll theme. You can find out more info about customizing your Jekyll theme, as well as basic Jekyll usage documentation at [jekyllrb.com](https://jekyllrb.com/)

# You can find the source code for Minima at GitHub

[jekyll][jekyll-organization] /
[minima](https://github.com/jekyll/minima)

## You can find the source code for Jekyll at GitHub

[jekyll][jekyll-organization] /
[jekyll](https://github.com/jekyll/jekyll)

[jekyll-organization]: https://github.com/jekyll

---

```bluespec
// 定义一个泛型函数，实现一个n位逐级传递加法器，输入参数是两个n位数和一个进位位
function Bit#(n+1) addN(Bit#(n) x, Bit#(n) y, Bit#(1) c0); 
  Bit#(n) s = 0; // 定义一个n位的和数变量，初始化为0
  Bit#(n+1) c = 0; // 定义一个(n+1)位的进位变量，初始化为0
  c[0] = c0; // 将输入的进位位赋给进位变量的最低位
  // 循环n次，每次处理一位加法，并处理进位
  for (Integer i=0; i<n; i=i+1) begin
    let cs = fa(x[i],y[i],c[i]); // 调用全加器函数fa处理当前位的加法和进位
    c[i+1] = cs[1]; // 将全加器返回的进位存储到进位变量的下一位
    s[i] = cs[0]; // 将全加器返回的和存储到和数变量的当前位
  end
  return {c[n],s}; // 返回一个(n+1)位的结果，最高位是最终的进位，其余位是和数
endfunction
```

```bluespec
module mkExample(Example);
    Reg#(Bit#(1)) some_state <- mkRegU;

    rule tick;
        some_state <= ~some_state;
    endrule
endmodule
```

```bluespec
module mkExample(Example);
    Reg#(Bit#(1)) some_state <- mkRegU;

    rule tick;
        some_state <= ~some_state;
    endrule
endmodule
```

`module mkExample(Example);`{:.language-bluespec .highlight}

---
<button class="btn js-toggle-dark-mode">Preview dark color scheme</button>

<script>
const toggleDarkMode = document.querySelector('.js-toggle-dark-mode');

jtd.addEvent(toggleDarkMode, 'click', function(){
  if (jtd.getTheme() === 'dark') {
    jtd.setTheme('light');
    toggleDarkMode.textContent = 'Preview dark color scheme';
  } else {
    jtd.setTheme('dark');
    toggleDarkMode.textContent = 'Return to the light side';
  }
});
</script>

Text can be **bold**, _italic_, or ~~strikethrough~~.

[Link to another page]({{site.baseurl}}/).

There should be whitespace between paragraphs.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

# [](#header-1)Header 1

This is a normal paragraph following a header. GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.

## [](#header-2)Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### [](#header-3)Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

为了使网站的字体更加适合显示中文内容，我们可以调整 $body-font-family 和 $mono-font-family 变量，包含一些更适合中文显示的字体选项。下面是修改后的字体设置，增加了一些常见的中文字体，如 Microsoft YaHei（微软雅黑）和 PingFang SC（苹方）等，同时保留了一些原有的西文字体以保证兼容性和备选：

#### [](#header-4-with-code-not-transformed)Header 4 `with code not transformed`

* This is an unordered list following a header.
* This is an unordered list following a header.
* This is an unordered list following a header.

##### [](#header-5)Header 5

1. This is an ordered list following a header.
2. This is an ordered list following a header.
3. This is an ordered list following a header.

###### [](#header-6)Header 6

[This is a very long link which wraps and therefore doesn't overflow
even when it comes at the beginning](.) of the line.

* [This is a very long link which wraps and therefore doesn't overflow the line
  when used first in an item ](.) in a list.

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this

* * *

### Here is an unordered list

* Item foo
* Item bar
* Item baz
* Item zip

### And an ordered list

1. Item one
1. Item two
1. Item three
1. Item four

### And an ordered list, continued

1. Item one
1. Item two

Some text

{:style="counter-reset:none"}

1. Item three
1. Item four

### And an ordered list starting from 42

{:style="counter-reset:step-counter 41"}

1. Item 42
1. Item 43
1. Item 44

### And a nested list

* level 1 item
  * level 2 item
  * level 2 item
    * level 3 item
    * level 3 item
* level 1 item
  * level 2 item
  * level 2 item
  * level 2 item
* level 1 item
  * level 2 item
  * level 2 item
* level 1 item

### Nesting an ol in ul in an ol

* level 1 item (ul)
  1. level 2 item (ol)
  1. level 2 item (ol)
  * level 3 item (ul)
  * level 3 item (ul)
* level 1 item (ul)
  1. level 2 item (ol)
  1. level 2 item (ol)
  * level 3 item (ul)
  * level 3 item (ul)
  1. level 4 item (ol)
  1. level 4 item (ol)
  * level 3 item (ul)
  * level 3 item (ul)
* level 1 item (ul)

### And a task list

* [ ] Hello, this is a TODO item
* [ ] Hello, this is another TODO item
* [x] Goodbye, this item is done

### Nesting task lists

* [ ] level 1 item (task)
  * [ ] level 2 item (task)
  * [ ] level 2 item (task)
* [ ] level 1 item (task)
* [ ] level 1 item (task)

### Nesting a ul in a task list

* [ ] level 1 item (task)
  * level 2 item (ul)
  * level 2 item (ul)
* [ ] level 1 item (task)
* [ ] level 1 item (task)

### Nesting a task list in a ul

* level 1 item (ul)
  * [ ] level 2 item (task)
  * [ ] level 2 item (task)
* level 1 item (ul)
* level 1 item (ul)

### Small image

![](../assets/images/small-image.jpg)

### Large image

![](../assets/images/large-image.jpg)

"[Wroclaw University Library digitizing rare archival texts](https://www.flickr.com/photos/97810305@N08/9401451269)" by [j_cadmus](https://www.flickr.com/photos/97810305@N08) is marked with [CC BY 2.0](https://creativecommons.org/licenses/by/2.0/?ref=openverse).

### Labels

I'm a label
{: .label }

blue
{: .label .label-blue }
green
{: .label .label-green }
purple
{: .label .label-purple }
yellow
{: .label .label-yellow }
red
{: .label .label-red }

**bold**
{: .label }
_italic_
{: .label }
_**bold + italic**_
{: .label }

### Definition lists can be used with HTML syntax

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

#### Multiple description terms and values

Term
: Brief description of Term

Longer Term
: Longer description of Term,
  possibly more than one line

Term
: First description of Term,
  possibly more than one line

: Second description of Term,
  possibly more than one line

Term1
Term2
: Single description of Term1 and Term2,
  possibly more than one line

Term1
Term2
: First description of Term1 and Term2,
  possibly more than one line

: Second description of Term1 and Term2,
  possibly more than one line

### More code

```python{% raw %}
def dump_args(func):
    "This decorator dumps out the arguments passed to a function before calling it"
    argnames = func.func_code.co_varnames[:func.func_code.co_argcount]
    fname = func.func_name
    def echo_func(*args,**kwargs):
        print fname, ":", ', '.join(
            '%s=%r' % entry
            for entry in zip(argnames,args) + kwargs.items())
        return func(*args, **kwargs)
    return echo_func

@dump_args
def f1(a,b,c):
    print a + b + c

f1(1, 2, 3)

def precondition(precondition, use_conditions=DEFAULT_ON):
    return conditions(precondition, None, use_conditions)

def postcondition(postcondition, use_conditions=DEFAULT_ON):
    return conditions(None, postcondition, use_conditions)

class conditions(object):
    __slots__ = ('__precondition', '__postcondition')

    def __init__(self, pre, post, use_conditions=DEFAULT_ON):
        if not use_conditions:
            pre, post = None, None

        self.__precondition  = pre
        self.__postcondition = post
{% endraw %}```

```

Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.

```

### Mermaid Diagrams

The following code is displayed as a diagram only when a `mermaid` key supplied in `_config.yml`.

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

### Collapsed Section

The following uses the [`<details>`](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/organizing-information-with-collapsed-sections) tag to create a collapsed section.

<details markdown="block">
<summary>Shopping list (click me!)</summary>

This is content inside a `<details>` dropdown.

* [ ] Apples
* [ ] Oranges
* [ ] Milk

</details>
