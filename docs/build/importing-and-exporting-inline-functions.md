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
ms.openlocfilehash: abb0443ab8fbd315524350caaff34e0250147ed2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328515"
---
# <a name="importing-and-exporting-inline-functions"></a>导入和导出内联函数

导入的函数可以定义为内联函数。 效果与内联定义标准函数大致相同;对函数的调用将扩展到内联代码中，就像宏一样。 这主要用作支持 DLL 中C++类的方法，这些类可能会内联其某些成员函数的效率。

导入的内联函数的一个功能是，您可以在C++中获取其地址。 编译器返回驻留在 DLL 中的内联函数副本的地址。 导入的内联函数的另一个功能是，您可以初始化导入函数的静态本地数据，这与全局导入的数据不同。

> [!CAUTION]
> 在提供导入的内联函数时，应小心谨慎，因为它们可能会造成版本冲突。 内联函数将扩展到应用程序代码中;因此，如果以后重写函数，则不会更新该函数，除非重新编译应用程序本身。 （通常，DLL 函数可以更新，而无需重新生成使用它们的应用程序。

## <a name="what-do-you-want-to-do"></a>您希望做什么？

- [从 DLL 导出](exporting-from-a-dll.md)

- [使用 从 DLL 导出。DEF 文件](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec（出口）从 DLL 导出](exporting-from-a-dll-using-declspec-dllexport.md)

- [使用AFX_EXT_CLASS导出和导入](exporting-and-importing-using-afx-ext-class.md)

- [导出C++函数，用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>另请参阅

[导入和导出](importing-and-exporting.md)
