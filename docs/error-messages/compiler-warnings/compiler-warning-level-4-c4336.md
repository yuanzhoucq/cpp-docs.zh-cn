---
title: 编译器警告（等级 4）C4336
ms.date: 11/04/2016
f1_keywords:
- C4336
helpviewer_keywords:
- C4336
ms.assetid: 93f199dd-d6dd-42c0-82d8-c12d101a7235
ms.openlocfilehash: 4946b932fa897dab057e430f16c781e2d06bebd0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484885"
---
# <a name="compiler-warning-level-4-c4336"></a>编译器警告（等级 4）C4336

导入交叉引用的类型库 type_lib1 导入 type_lib2 之前

类型库引用与[#import](../../preprocessor/hash-import-directive-cpp.md)指令。 但是，类型库包含对使用未引用的另一个类型库的引用`#import`。 编译器找到此其他.tlb 文件。

从以下两个文件 （使用 midl.exe 编译） 创建的磁盘上的给定两个类型库：

```
// c4336a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library c4336aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C4336
   {
      one, two, three
   };
};
```

第二个类型库：

```
// c4336b.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4336bLib
{
   importlib ("c4336a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4336
   {
      enum E_C4336 e;
   };
};
```

下面的示例生成 C4336:

```
// C4336.cpp
// compile with: /W4 /LD
// #import "C4336a.tlb"
#import "C4336b.tlb"   // C4336, uncomment previous line to resolve
```