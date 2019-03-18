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
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812429"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>导出 C 函数以用于 C 或 C++ 语言可执行文件

如果想要从 C 语言或 c + + 语言模块访问，则应使用以 C 编写的 DLL 中的函数 **__cplusplus**预处理器宏，以确定哪种语言正在编译，然后再声明这些带 C 链接如果要从 c + + 语言模块使用的函数。 如果使用此方法并提供适合您的 DLL 的标头文件，这些函数可供 C 和 c + + 用户需进行任何更改。

下面的代码显示了可由 C 和 c + + 客户端应用程序的标头文件：

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

如果需要链接到可执行文件在 c + + 的 C 函数，并且函数声明标头文件未使用上面的技术，c + + 源代码文件中，执行以下操作来阻止编译器修饰 C 函数名：

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

- [导入到使用 __declspec （dllimport） 的应用程序](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [修饰的名](reference/decorated-names.md)

- [使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>请参阅

[从 DLL 导出](exporting-from-a-dll.md)
