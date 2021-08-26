---
title: Writing a New Post
author: Cotes Chung
date: 2019-08-08 14:10:00 +0800
categories: [Blogging, Tutorial]
tags: [writing]
---

# 한글 테스트
## _기울어진 한글_
한글 본문입니다
월 26일 오후 7시 5분 인천국제공항 1층. 아프가니스탄에서 온 A씨는 양 손 짐을 가득 넣은 여행용 가방과 백팩을 들고 E 입국장 문을 통과했다. 아내 B씨는 아직 머리털도 채 다 나지 않은 아이를 안고 그를 따랐다. 가족은 방역복을 입은 경찰 안내에 따라 건물 밖 버스로 향했다. 이들은 10~20명씩 나뉘어 차례대로 입국 심사, PCR 검사를 받고 입국장을 통과했다..
```c
int a; // 한글 주석
>???
printf("%d",a);
```


## Naming and Path

Create a new file named `YYYY-MM-DD-TITLE.EXTENSION` and put it in the `_posts/` of the root directory. Please note that the `EXTENSION` must be one of `md` and `markdown`.

## Front Matter

Basically, you need to fill the [Front Matter](https://jekyllrb.com/docs/front-matter/) as below at the top of the post:

```yaml
---
title: TITLE
date: YYYY-MM-DD HH:MM:SS +/-TTTT
categories: [TOP_CATEGORIE, SUB_CATEGORIE]
tags: [TAG]     # TAG names should always be lowercase
---
```

> **Note**: The posts' ***layout*** has been set to `post` by default, so there is no need to add the variable ***layout*** in Front Matter block.

### Timezone of date

In order to accurately record the release date of a post, you should not only setup the `timezone` of `_config.yml` but also provide the the post's timezone in field `date` of its Front Matter block. Format: `+/-TTTT`, e.g. `+0800`.

### Categories and Tags

The `categories` of each post is designed to contain up to two elements, and the number of elements in `tags` can be zero to infinity. For instance:

```yaml
categories: [Animal, Insect]
tags: [bee]
```

## Table of Contents

By default, the **T**able **o**f **C**ontents (TOC) is displayed on the right panel of the post. If you want to turn it off globally, go to `_config.yml` and set the value of variable `toc` to `false`. If you want to turn off TOC for specific post, add the following to post's [Front Matter](https://jekyllrb.com/docs/front-matter/):

```yaml
---
toc: false
---
```

## Comments

Similar to TOC, the [Disqus](https://disqus.com/) comments is loaded by default in each post, and the global switch is defined by variable `comments` in file `_config.yml` . If you want to close the comment for specific post, add the following to the **Front Matter** of the post:

```yaml
---
comments: false
---
```

## Mathematics

For website performance reasons, the mathematical feature won't be loaded by default. But it can be enabled by:

```yaml
---
math: true
---
```

## Mermaid

[**Mermaid**](https://github.com/mermaid-js/mermaid) is a great diagrams generation tool. To enable it on your post, add the following to the YAML block:

```yml
---
mermaid: true
---
```

Then you can use it like other markdown language: surround the graph code with ```` ```mermaid ```` and ```` ``` ````.

## Images

### Preview image

If you want to add an image to the top of the post contents, specify the attribute `src`, `width`, `height` and `alt` for the image:

```yaml
---
image:
  src: /path/to/image/file
  width: 1000   # in pixels
  height: 400   # in pixels
  alt: image alternative text
---
```

Except for `alt`, all other options are necessary, especially the `width` and `height`, which are related to user experience and web page loading performance. Later section ["Image size"](#image-size) will also mention this.


### Image caption

Add italics to the next line of an image，then it will become the caption and appear at the bottom of the image:

```markdown
![img-description](/path/to/image)
_Image Caption_
```

### Image size

In order to prevent the page content layout from shifting when the image is loaded, we should set the width and height for each image:

```markdown
![Desktop View](/assets/img/sample/mockup.png){: width="700" height="400" }
```

### Image position

By default, the image is centered, but you can specify the position by using one of class `normal` , `left` and `right`. For example:

- **Normal position**

  Image will be left aligned in below sample:

  ```markdown
  ![Desktop View](/assets/img/sample/mockup.png){: .normal }
  ```

- **Float to the left**

  ```markdown
  ![Desktop View](/assets/img/sample/mockup.png){: .left }
  ```

- **Float to the right**

  ```markdown
  ![Desktop View](/assets/img/sample/mockup.png){: .right }
  ```

> **Limitation**: Once you specify the position of an image, it is forbidden to add the image caption.

### Image shadow

The screenshots of the program window can be considered to show the shadow effect, and the shadow will be visible in the `light` mode:

```markdown
![Desktop View](/assets/img/sample/mockup.png){: .shadow }
```

### CDN URL

If you host the images on the CDN, you can save the time of repeatedly writing the CDN url by assigning the variable `img_cdn` of `_config.yml` file:

```yaml
img_cdn: https://cdn.com
```

Once `img_cdn` is assigned, the CDN url will be added to the path of all images (images of site avatar and posts) starting with `/`.

For instance, when using images:

```markdown
![The flower](/path/to/flower.png)
```

The parsing result will automatically add the CDN prefix `https://cdn.com` before the image path:

```html
<img src="https://cdn.com/path/to/flower.png" alt="The flower">
```

## Pinned Posts

You can pin one or more posts to the top of the home page, and the fixed posts are sorted in reverse order according to their release date. Enable by:

```yaml
---
pin: true
---
```

## Code Block

Markdown symbols ```` ``` ```` can easily create a code block as following examples.

```
This is a common code snippet, without syntax highlight and line number.
```

## Specific Language

Using ```` ```language ```` you will get code snippets with line numbers and syntax highlight.

> **Note**: The Jekyll style `{% raw %}{%{% endraw %} highlight LANGUAGE {% raw %}%}{% endraw %}` or `{% raw %}{%{% endraw %} highlight LANGUAGE linenos {% raw %}%}{% endraw %}` are not allowed to be used in this theme !

```yaml
# Yaml code snippet
items:
    - part_no:   A4786
      descrip:   Water Bucket (Filled)
      price:     1.47
      quantity:  4
```

### Liquid Codes

If you want to display the **Liquid** snippet, surround the liquid code with `{% raw %}{%{% endraw %} raw {%raw%}%}{%endraw%}` and `{% raw %}{%{% endraw %} endraw {%raw%}%}{%endraw%}` .

{% raw %}
```liquid
{% if product.title contains 'Pack' %}
  This product's title contains the word Pack.
{% endif %}
```
{% endraw %}

## Learn More

For more knowledge about Jekyll posts, visit the [Jekyll Docs: Posts](https://jekyllrb.com/docs/posts/).

