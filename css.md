# CSS 特性

仅在支持该特性的浏览器中使用

  ```css
  @supports (property) {
    property: somthing;
  }
  ```

避免因页面长度不同而导致滚动条有无，而对布局产生影

  ```css
  html {
    scrollbar-gutter: stable;
  }
  ```

- 在写新博客的时候，用了这个。由于我设置了一个 `<header>` 始终置顶，这时问题出现了。`stable` 保证布局不受滚动条存在影响的原因就是它实际上是占了滚动条位置的空白元素。

  滚动条默认是在内容层中的，而非在内容层上。这导致当一个页面没有滚动条时，`<header>` 最右侧就会出现一个滚动条宽度的空白。`<header>` 与 `<body>` 背景颜色不同时格外明显。

   我的博客是拿 Nuxt 写的，不知道这里怎么写我就先去写别的组件了。正好在看文档时发现了 Nuxt 文档实现了类似的效果，一看是用了 [`overflow: overlay;`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/overflow)。这个值使得滚动条和内容分层了，前面的问题自然也就解决了。

   但可惜的一点就是在最新的 CSS 标准中该值已经被废弃了，不过浏览器中仅有 IE 和 Firefox 不支持，CSS 标准和浏览器实现间还是有段不小的距离的。

   这种实现方式还是让我不太舒服，就继续老老实实使用默认值。反正滚动条不会对我博客的布局产生影响，归根到底只是发现这个新特性想尝尝鲜罢了，没有一定要使用的必要。

   -----

  在调整滚动条和 `<header>` 矛盾中间我也对滚动条的样式进行了调整。用的是 [`::webkit-scrollbar` 伪类](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::-webkit-scrollbar)，Chrome 默认滚动条傻大黑粗，反倒是 Firefox 的看着小巧美观些。我个人使用时会[开启 Overlay Scrollbars](chrome://flags/#overlay-scrollbars)，其实就是全局使用上面提到的那个 `overflow:overlay;` 属性。不过考虑到样式统一的问题就自己改改样式。

  `::webkit` 伪类看名字也能知道仅 Webkit 系浏览器支持，Firefox 再次不支持。本来调整滚动条样式就是保持各端渲染一致，既然做不到那就摆烂了。

  中间也有发现两个在 CSS 标准中，但目前仅 Firefox 支持的属性 [`scrollbar-width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/scrollbar-width) 和 [`scrollbar-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/scrollbar-color)，原先想着如果颜色和宽度能够统一那效果应该也差不多。但实际尝试中发现在我所使用的基于 Firefox 的 LibreWolf 中也并不支持，LibreWolf 是对 Firefox 在隐私方面的进一步改进，按理来说 CSS 渲染应该是和上游保持一致的。

  所以应该是 MDN 的兼容性表格过时了，不过也有可能是 LibreWolf 的问题，我也没有去 Firefox 上验证，毕竟再下一个浏览器也太麻烦了吧。

   -----

  最后绕了一大圈还是回到了原点，默认值果然还是适合大多数情况。而各浏览器实现和 CSS 标准间的割裂也属实让人头疼。
  
  值得一提的是你现在看到的这个页面也用了 `::webkit-scrollbar` 伪类，小巧且不引人注意的滚动条才应该是滚动条的最终形态。因为这个样式 Logseq 自带的所以我也就没有去改，傻大黑粗、千人千面的滚动条就留给我自己写的博客吧。

原生强调色

  ```css
  body {
    accent-color: black;
  }
  ```
