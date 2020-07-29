---
title: 使用 dllexport 和 dllimport 定义内联 C++ 函数
ms.date: 11/04/2016
helpviewer_keywords:
- inline functions [C++], defining
- functions [C++], defining inline
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
ms.assetid: 3b48678b-e7b8-4eda-bb46-b5d34dcf7817
ms.openlocfilehash: cf3c73e21834391d894a2924f78f6e6143c3a2b6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221713"
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>使用 dllexport 和 dllimport 定义内联 C++ 函数

**Microsoft 专用**

您可以使用属性将函数定义为内联 **`dllexport`** 。 在这种情况下，将始终实例化并导出该函数，无论程序中是否有模块引用该函数。 假定该函数由另一个程序导入。

你还可以将定义为内联一个使用特性声明的函数 **`dllimport`** 。 在这种情况下，该函数可以展开（遵从 /Ob 规范），但决不实例化。 具体而言，如果采用内联导入函数的地址，则返回驻留在 DLL 中的函数地址。 此行为与采用非内联导入函数的地址相同。

这些规则适用于其定义出现在类定义中的内联函数。 此外，内联函数中的静态本地数据和字符串在 DLL 和客户端之间保持的标识与它们在单一程序（即，没有 DLL 接口的可执行文件）中保持的一样。

在提供导入的内联函数时谨慎操作。 例如，如果更新 DLL，请不要假定该客户端将使用更改后的 DLL 版本。 若要确保加载 DLL 的适当版本，请重新生成 DLL 的客户端。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[dllexport、dllimport](../cpp/dllexport-dllimport.md)
