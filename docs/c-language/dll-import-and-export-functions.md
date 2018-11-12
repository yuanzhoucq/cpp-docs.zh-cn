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
ms.openlocfilehash: b4f0674e68f2c7b8deeae663c42470b83777ac78
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572377"
---
# <a name="dll-import-and-export-functions"></a>DLL 导入和导出函数

**Microsoft 专用**

有关本主题的最完整且最新的信息可在 [dllexport、dllimport](../cpp/dllexport-dllimport.md) 中找到。

dllimport 和 `dllexport` 存储类修饰符是 C 语言的 Microsoft 专用扩展。 这些修饰符显式定义了 DLL 与其客户端（可执行文件或另一个 DLL）的接口。 如果将函数声明为 `dllexport`，则不再需要模块定义 (.DEF) 文件。 还可以将 dllimport 和 `dllexport` 修饰符用于数据和对象。

dllimport 和 `dllexport` 存储类修饰符必须与扩展特性语法关键字 `__declspec` 一起使用，如以下示例中所示：

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