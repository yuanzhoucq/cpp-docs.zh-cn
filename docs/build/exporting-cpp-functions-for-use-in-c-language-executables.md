---
title: 导出 C++ 函数以用于 C 语言可执行文件
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
ms.openlocfilehash: eaa742fc2738ef4aeeb54bb8fd2b0da923ac57de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667423"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>导出 C++ 函数以用于 C 语言可执行文件

如果您具有函数编写 c + + 中，你想要访问 C 语言模块中，应声明这些函数具有 C 链接而不是 c + + 链接的 DLL 中。 除非另行指定，否则 c + + 编译器将使用 c + + 类型安全命名 （也称为名称修饰） 和 c + + 调用约定，这可能很难从 C.调用

若要指定 C 链接，请指定`extern "C"`函数声明的。 例如：

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用.def 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [导出和导入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [导出 C 函数以用于 C 或 c + + 语言可执行文件](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)

- [导入到使用 __declspec （dllimport） 的应用程序](../build/importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [修饰的名](../build/reference/decorated-names.md)

- [使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>请参阅

[从 DLL 导出](../build/exporting-from-a-dll.md)