---
title: 按序号而不是按名称从 DLL 导出函数
ms.date: 11/04/2016
f1_keywords:
- NONAME
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 6a5ac13fdc85b3cb1626aefa28b92866a8c856c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503411"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>按序号而不是按名称从 DLL 导出函数

从 DLL 导出函数的最简单方法是将其导出的名称。 这是在使用时，会发生什么情况 **__declspec （dllexport)**，例如。 但可以改为按序号导出函数。 通过此方法，必须使用.def 文件而不是 **__declspec （dllexport)**。 若要指定函数的序号值，将其序号追加到.def 文件中的函数名称。 有关指定序号的信息，请参阅[使用.def 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)。

> [!TIP]
>  如果你想要优化您的 DLL 文件的大小，使用**NONAME**上每个导出函数的属性。 与**NONAME**属性，将其序号存储在 DLL 的导出表而不是函数名称。 如果要导出很多函数，这可以是相当大的节省。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用.def 文件，因此我可以按序号导出](../build/exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport）](../build/exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>请参阅

[从 DLL 导出](../build/exporting-from-a-dll.md)