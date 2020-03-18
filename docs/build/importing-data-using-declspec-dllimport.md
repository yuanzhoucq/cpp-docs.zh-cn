---
title: 使用 __declspec(dllimport) 导入数据
ms.date: 11/04/2016
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: c9dce798572a91bcb9721f022393abb669970131
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440456"
---
# <a name="importing-data-using-__declspecdllimport"></a>使用 __declspec(dllimport) 导入数据

对于数据，使用 **__declspec （dllimport）** 是删除间接层的便利项。 从 DLL 导入数据时，您仍需要浏览导入地址表。 在 **__declspec （dllimport）** 之前，这意味着您必须在访问从 DLL 导出的数据时，执行额外级别的间接寻址：

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

然后导出中的数据。DEF 文件：

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

并在 DLL 外部访问它：

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

将数据标记为 **__declspec （dllimport）** 时，编译器会自动为你生成间接代码。 您不必再担心以上步骤。 如前文所述，在生成 DLL 时不要对数据使用 **__declspec （dllimport）** 声明。 DLL 中的函数不使用导入地址表来访问数据对象;因此，不会有额外的间接寻址级别。

若要从 DLL 自动导出数据，请使用以下声明：

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>另请参阅

[导入到应用程序中](importing-into-an-application.md)
