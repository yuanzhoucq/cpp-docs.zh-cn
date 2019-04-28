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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273568"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>导出 C 函数以用于 C 或 C++ 语言可执行文件

如果在 DLL 中的函数在你想要从 C 语言访问 C 或C++语言模块，你应使用 **__cplusplus**预处理器宏，以确定哪种语言正在编译，然后再声明这些如果要使用从带 C 链接函数C++语言模块。 如果使用此方法并提供适合您的 DLL 的标头文件，可以通过 C 使用这些函数和C++用户需进行任何更改。

下面的代码演示可由 C 标头文件和C++客户端应用程序：

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

如果需要链接到 C 函数在C++可执行文件和函数声明标头文件没有使用上述的技术，在C++源文件中，执行以下操作来阻止编译器修饰 C 函数名：

```cpp
extern "C" {
#include "MyCHeader.h"
}
```

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用.def 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport） 从 DLL 导出](exporting-from-a-dll-using-declspec-dllexport.md)

- [导出和导入使用 AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [修饰的名](reference/decorated-names.md)

- [使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>请参阅

[从 DLL 导出](exporting-from-a-dll.md)
