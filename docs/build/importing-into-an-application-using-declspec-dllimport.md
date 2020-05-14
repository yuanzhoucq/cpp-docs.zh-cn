---
title: 使用 __declspec(dllimport) 导入到应用程序中
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
ms.openlocfilehash: fd7d42ec5a76b92aa789a3a20f38e6b2c0fd2cb1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440406"
---
# <a name="import-into-an-application-using-__declspecdllimport"></a>使用 __declspec(dllimport) 导入到应用程序中

使用由 DLL 定义的公共符号的程序会导入它们。 为使用 DLL 生成的应用程序创建头文件时，可在公共符号的声明中使用 __declspec(dllimport)  。 无论是使用 .def 文件还是 __declspec(dllexport)  关键字导出，关键字 __declspec(dllimport)  都有效。

若要使代码更具可读性，请为 __declspec(dllimport)  定义宏，然后使用宏声明每个导入的符号：

```
#define DllImport   __declspec( dllimport )

DllImport int  j;
DllImport void func();
```

使用 __declspec(dllimport)  在函数声明中是可选的，但如果使用此关键字，则编译器将生成更高效的代码。 但是，必须将 __declspec(dllimport)  用于导入可执行文件，以访问 DLL 的公共数据符号和对象。 请注意，DLL 的用户仍需要与导入库链接。

可以对 DLL 和客户端应用程序使用相同的头文件。 为此，请使用特殊的预处理器符号来指示是生成 DLL 还是生成客户端应用程序。 例如：

```
#ifdef _EXPORTING
   #define CLASS_DECLSPEC    __declspec(dllexport)
#else
   #define CLASS_DECLSPEC    __declspec(dllimport)
#endif

class CLASS_DECLSPEC CExampleA : public CObject
{ ... class definition ... };
```

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [导入和导出内联函数](importing-and-exporting-inline-functions.md)

- [相互导入](mutual-imports.md)

## <a name="see-also"></a>请参阅

[导入到应用程序中](importing-into-an-application.md)
