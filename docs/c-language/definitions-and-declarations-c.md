---
title: 定义和声明 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
ms.openlocfilehash: 0e39832f942eb1473be913112fde1d37ddf05674
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226361"
---
# <a name="definitions-and-declarations-c"></a>定义和声明 (C)

**Microsoft 专用**

DLL 接口引用已知由系统中的某程序导出的所有项（函数和数据）；即所有被声明为 `dllimport` 或 `dllexport` 的项。 DLL 接口中包含的所有声明都必须指定 `dllimport` 或 `dllexport` 特性。 但是，定义仅可指定 `dllexport` 特性。 例如，以下函数定义产生了一个编译器错误：

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int func()    /* Error; dllimport prohibited in */
                        /* definition. */
{
   return 1;
}
```

以下代码也会产生错误：

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int i = 10;      /* Error; this is a definition. */
```

但是，这是正确的语法：

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport int i = 10;      /* Okay: this is an export definition. */
```

使用 `dllexport` 意味着定义，而使用 `dllimport` 则意味着声明。 必须结合使用 `extern` 关键字和 `dllexport` 来强制声明；否则意味着定义。

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllImport int k;   /* These are correct and imply */
Dllimport int j;          /* a declaration. */
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[DLL 导入和导出函数](../c-language/dll-import-and-export-functions.md)
