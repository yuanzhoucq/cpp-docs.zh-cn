---
title: 按序号而不是按名称从 DLL 导出函数
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 66e99b18d181e9067e90398c35a61db2da66c301
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328576"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>按序号而不是按名称从 DLL 导出函数

从 DLL 导出函数的最简单方法是按名称导出它们。 例如，当您使用 **__declspec（dllexport）** 时，就会发生这种情况。 但是，您可以改为按元数导出函数。 使用此技术，必须使用 .def 文件而不是 **__declspec（dllexport）**。 要指定函数的元数值，请将其元数追加到 .def 文件中的函数名称。 有关指定位数的信息，请参阅[从 DLL 导出使用 .def 文件](exporting-from-a-dll-using-def-files.md)。

> [!TIP]
> 如果要优化 DLL 的文件大小，请使用每个导出函数上的**NONAME**属性。 使用**NONAME**属性时，这些表存储在 DLL 的导出表中，而不是函数名称中。 如果您要导出许多函数，这可以节省大量成本。

## <a name="what-do-you-want-to-do"></a>您希望做什么？

- [使用 .def 文件，以便我可以通过 ddinal 导出](exporting-from-a-dll-using-def-files.md)

- [使用__declspec（出口）](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>另请参阅

[从 DLL 导出](exporting-from-a-dll.md)
