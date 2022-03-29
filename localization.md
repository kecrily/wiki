# 本地化怎么做？

- 数字&货币：[`Number.prototype.toLocaleString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toLocaleString)
- 时间&时区：[`Intl.DateTimeFormat`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat)

在中文和西文间进行转换时，需要注意斜体样式的转换。有部分译者会生硬地将样式直接改为粗体或衬线体，但根据在西文中斜体的具体用法进行判断转换方式更为妥当。

- 作品加书名号
- 特定运载工具、外来词清除样式
- 强调加粗
