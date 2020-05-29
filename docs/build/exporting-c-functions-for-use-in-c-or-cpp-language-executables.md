---
title: 导出 C 函数以用于 C 或 C++ 语言可执行文件
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
ms.openlocfilehash: b7ba2ed30615efb3b05e71cecf0ea69898feb8ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273568"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>导出 C 函数以用于 C 或 C++ 语言可执行文件

如果使用 C 编写的 DLL 中的函数需要从 C 语言或 C++ 语言模块进行访问，则应使用 __cplusplus  预处理器宏来确定所编译的语言，然后使用 C 链接声明这些函数（如果从 C++ 语言模块进行使用）。 如果使用此方法并为 DLL 提供头文件，则 C 和 C++ 用户可以在不进行任何更改的情况下使用这些函数。

下面的代码演示 C 和 C++ 客户端应用程序可以使用的头文件：

```h
// MyCFuncs.h
#ifdef __cplusplus
extern "C" {  // only need to export C interface if
              // used by C++ source code
#endif

__declspec( dllimport ) void MyCFunc();
__declspec( dllimport ) void AnotherCFunc();

#ifdef __cplusplus
}
#endif
```

如果需要将 C 函数链接到 C++ 可执行文件，并且函数声明头文件未使用上述方法，请在 C++ 源文件中执行以下操作，以防止编译器修饰 C 函数名称：

```cpp
extern "C" {
#include "MyCHeader.h"
}
```

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用 .def 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec(dllexport) 从 DLL 导出](exporting-from-a-dll-using-declspec-dllexport.md)

- [使用 AFX_EXT_CLASS 导出和导入](exporting-and-importing-using-afx-ext-class.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [修饰名](reference/decorated-names.md)

- [使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>请参阅

[从 DLL 导出](exporting-from-a-dll.md)
