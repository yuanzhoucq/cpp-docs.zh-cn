---
title: 使用 __declspec （dllimport） 导入数据 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a024d7488eb1683f40548839ab843da1e56f65e8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710211"
---
# <a name="importing-data-using-declspecdllimport"></a>使用 __declspec(dllimport) 导入数据

在使用的数据的情况下 **__declspec （dllimport)** 是一个间接层中删除的方便项。 将数据导入从 DLL 中，您仍需要通过导入地址表。 之前 **__declspec （dllimport)**，这意味着您必须记得要访问的数据从 DLL 导出时执行更高级别的间接寻址：

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

然后会在将数据导出应用。DEF 文件：

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

和 DLL 的外部访问它：

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

当将数据作为 **__declspec （dllimport)**，编译器自动为您生成的间接寻址代码。 不再需要担心上述步骤。 如前面所述，不使用 **__declspec （dllimport)** 生成 DLL 时对数据的声明。 DLL 中的函数不使用导入地址表来访问数据的对象;因此，您不会额外级别的间接寻址存在。

若要从 DLL 自动导出数据，使用此声明：

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>请参阅

[导入到应用程序中](../build/importing-into-an-application.md)