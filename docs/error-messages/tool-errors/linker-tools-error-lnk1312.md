---
title: 链接器工具错误 LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: 49fa7e7963d6bb561e1602b58fe1f26c5f3d54bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160466"
---
# <a name="linker-tools-error-lnk1312"></a>链接器工具错误 LNK1312

无效或损坏的文件： 无法导入程序集

生成程序集、 模块或使用编译的程序集之外的文件时 **/clr**传递给 **/ASSEMBLYMODULE**链接器选项。  如果传递到的对象文件 **/ASSEMBLYMODULE**，只是该对象直接传递到链接器，而不是向 **/ASSEMBLYMODULE**。

## <a name="example"></a>示例

下面的示例创建的.obj 文件。

```
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

## <a name="example"></a>示例

下面的示例生成 LNK1312。

```
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```