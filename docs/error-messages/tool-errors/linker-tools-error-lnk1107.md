---
title: 链接器工具错误 LNK1107
ms.date: 11/04/2016
f1_keywords:
- LNK1107
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
ms.openlocfilehash: c75966d9c6c22f1bd2123fb30282bb2bed467130
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991027"
---
# <a name="linker-tools-error-lnk1107"></a>链接器工具错误 LNK1107

无效或损坏的文件：无法在位置读取

该工具无法读取文件。 重新创建文件。

如果尝试将使用[/clr： noAssembly](../../build/reference/clr-common-language-runtime-compilation.md)或[/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)创建的模块（.dll 或 .netmodule 扩展传递到链接器），也可能会发生 LNK1107;改为传递 .obj 文件。

如果编译下面的示例：

```cpp
// LNK1107.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

然后在命令行上指定**LINK LNK1107** ，将获取 LNK1107。  若要解决此错误，请改为指定**链接 LNK1107** 。
