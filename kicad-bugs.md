# KiCAD Bugs

## 1. Tracks ends too close

**描述：**当采用差分布线时，会出现`kicad two track ends too close`的错误。

**复现：**设置diff pairs的宽度为0.16，间距（clearance）为0.24，随便布线，在拐角或者端点，进行DRC报错时会出错。

**链接：**[DRC violation with differential pair router](https://bugs.launchpad.net/kicad/+bug/1533551)

```note
I experienced the same issue when I was doing a BGA fanout. I suspect the problem migth be with floating point dimensions comparison as when I decreased minimal clearance from 0.1 mm to 0.099 mm it went OK.
```

**解决办法：**可能是由浮点判断错误导致的，在布局完毕后，将clearance减少一点，例如`2.399`，即可消除错误。
