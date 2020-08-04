---
title: 使用 __declspec(dllimport) 导入到应用程序中
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
ms.openlocfilehash: 50b630334cfd8752935b54549190d698fa5136bb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223975"
---
# <a name="import-into-an-application-using-__declspecdllimport"></a>使用 __declspec(dllimport) 导入到应用程序中

使用由 DLL 定义的公共符号的程序会导入它们。 在为使用 DLL 生成的应用程序创建头文件时，请在公共符号的声明中使用 `__declspec(dllimport)`。 无论使用 .def 文件还是 `__declspec(dllexport)` 关键字进行导出，都可以使用关键字 `__declspec(dllimport)`。

为了提高代码的可读性，请为 `__declspec(dllimport)` 定义宏，并使用此宏来声明导入的每个符号：

```
#define DllImport   __declspec( dllimport )

DllImport int  j;
DllImport void func();
```

虽然在函数声明中使用 `__declspec(dllimport)` 是可选的，但如果你使用此关键字，编译器会生成更高效的代码。 不过，必须对导入的可执行文件使用 `__declspec(dllimport)`，以访问 DLL 的公共数据符号和对象。 请注意，DLL 的用户仍需要与导入库链接。

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
