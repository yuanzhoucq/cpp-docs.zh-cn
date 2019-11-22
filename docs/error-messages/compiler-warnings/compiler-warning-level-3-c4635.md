---
title: 编译器警告（等级 3）C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: b6fd45dc6c28c0d12eb2b2991f8a087b1841d1a9
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189144"
---
# <a name="compiler-warning-level-3-c4635"></a>编译器警告（等级 3）C4635

XML 文档注释目标: XML 格式不正确: 原因

编译器发现此 XML 标记存在一些问题。  解决该问题并重新编译

下面的示例生成 C4635：

```cpp
// C4635.cpp
// compile with: /doc /clr /W3 /c
/// <summary>
/// The contents of the folder have changed.
/// <summary/>   // C4635

// try the following line instead
// /// </summary>
public ref class Test {};
```

请注意，此示例的输出显示： **结束标记“member”与开始标记“summary”不匹配。**

The problem with this sample is that the end tag for \<summary> is poorly formed, and the compiler does not recognize it as the \<summary> end tag.  The \<member> tag is embedded in the .xdc file by the compiler in every /doc compilation.  So, the problem here is that the end tag \</member>, does not match the previous start tag that the compiler processed (\<summary>.