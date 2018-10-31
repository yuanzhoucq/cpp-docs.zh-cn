---
title: 导入和导出内联函数
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
ms.openlocfilehash: 407ca39aa53cf622b531fa0ca7818682c82c561f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439099"
---
# <a name="importing-and-exporting-inline-functions"></a>导入和导出内联函数

可以为内联定义导入的函数。 效果大致是相同定义标准函数内联;对函数的调用会展开为内联代码，类似于宏。 这是主要有用，因为一种方法支持 c + + DLL 中可能会内联类及其成员的一些函数以提高效率。

导入的内联函数的一个功能是您可以在 c + + 中采用其地址。 编译器返回的副本驻留在 DLL 中的内联函数的地址。 导入的内联函数的另一个功能是函数的可以初始化静态本地数据的导入，与全局导入的数据不同。

> [!CAUTION]
>  在提供导入内联函数，因为他们可以创建可能发生版本冲突时应十分小心。 内联函数获取扩展为应用程序代码;因此，如果您更高版本重写函数，它不会更新除非重新编译应用程序本身。 （通常情况下，DLL 函数可以更新而重新生成的应用程序使用它们。）

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [从 DLL 导出](../build/exporting-from-a-dll.md)

- [导出从 DLL 使用。DEF 文件](../build/exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [导出和导入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [导出 c + + 函数以用于 C 语言可执行文件](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)

- [导入到使用 __declspec （dllimport） 的应用程序](../build/importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>请参阅

[导入和导出](../build/importing-and-exporting.md)