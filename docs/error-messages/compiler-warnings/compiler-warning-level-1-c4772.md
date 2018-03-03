---
title: "编译器警告 （等级 1） C4772 |Microsoft 文档"
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: error-reference
f1_keywords:
- C4772
dev_langs:
- C++
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 631cd4f872c7b8912b791417c04f6c6e9e056bdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4772"></a>编译器警告（等级 1）C4772

> \#导入从缺少的类型库; 引用了类型*缺少类型*用作占位符

类型库引用与[#import](../../preprocessor/hash-import-directive-cpp.md)指令。 但是，类型库包含对另一个使用未被引用的类型库的引用`#import`。 由编译器找不到此其他.tlb 文件。

请注意，编译器将不到类型库的不同目录是否你使用[/I （附加包含目录）](../../build/reference/i-additional-include-directories.md)编译器选项来指定这些目录。 如果你想要在不同的目录中查找类型库编译器，则将这些目录添加到 PATH 环境变量。

默认情况下作为错误发出此警告。 C4772 不能用 /w0 取消显示被取消。

## <a name="example"></a>示例

这是再现 C4772 所需的第一个类型库。

```IDL
// c4772a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C4772aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c100")]
   enum E_C4772a
   {
      one, two, three
   };
};
```

这是再现 C4772 所需的第二个类型库。

```IDL
// c4772b.idl
// post-build command: del /f C4772a.tlb
// C4772a.tlb is available when c4772b.tlb is built
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4772bLib
{
   importlib ("c4772a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4772b
   {
      enum E_C4772a e;
   };
};
```

下面的示例生成 C4772:

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```