---
title: DLL 导入和导出函数
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], importing
- dllimport attribute [C++], storage-class attribute
- DLL exports [C++]
- declaring functions, with dllexport and dllimport
- extended storage-class attributes
- dllexport attribute [C++], storage-class attribute
ms.assetid: 08d164b9-770a-4e14-afeb-c6f21d9e33e4
ms.openlocfilehash: 753a51fa8e2c87b77a54e5e93522e5f11585b610
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200070"
---
# <a name="dll-import-and-export-functions"></a>DLL 导入和导出函数

**Microsoft 专用**

有关本主题的最完整且最新的信息可在 [dllexport、dllimport](../cpp/dllexport-dllimport.md) 中找到。

`dllimport` 和 `dllexport` 存储类修饰符是 Microsoft 对 C 语言的特定扩展。 这些修饰符显式定义了 DLL 与其客户端（可执行文件或另一个 DLL）的接口。 如果将函数声明为 `dllexport`，则不再需要模块定义 (.DEF) 文件。 还可以对数据和对象使用 `dllimport` 和 `dllexport` 修饰符。

`dllimport` 和 `dllexport` 存储类修饰符必须与扩展的特性语法关键字 `__declspec` 一起使用，如下面的示例所示：

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllExport int j;
DllExport int n;
```

有关扩展的存储类修饰符的语法的特定信息，请参阅[扩展的存储类特性](../c-language/c-extended-storage-class-attributes.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[C 函数定义](../c-language/c-function-definitions.md)
