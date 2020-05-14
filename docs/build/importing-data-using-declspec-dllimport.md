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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440456"
---
# <a name="importing-data-using-__declspecdllimport"></a>使用 __declspec(dllimport) 导入数据

对于数据，使用 __declspec(dllimport) 是删除间接寻址层的便捷项  。 从 DLL 导入数据时，仍必须浏览导入地址表。 在使用 __declspec(dllimport) 之前，这意味着访问从 DLL 导出的数据时，必须执行额外级别的间接寻找  ：

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

然后导出 .DEF 文件中的数据：

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

并从 DLL 外部访问它：

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

将数据标记为 __declspec(dllimport) 时，编译器会自动为你生成间接寻址代码  。 你不必再担心以上步骤。 如前所述，在生成 DLL 时，请不要对数据使用 __declspec(dllimport) 声明  。 DLL 中的函数不会使用导入地址表来访问数据对象；因此，不会有额外级别的间接寻出现。

若要从 DLL 中自动导出数据，请使用以下声明：

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>请参阅

[导入到应用程序中](importing-into-an-application.md)
