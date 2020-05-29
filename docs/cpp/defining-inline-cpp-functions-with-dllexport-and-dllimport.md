---
title: 使用 dllexport 和 dllimport 定义内联 C++ 函数
ms.date: 11/04/2016
helpviewer_keywords:
- inline functions [C++], defining
- functions [C++], defining inline
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
ms.assetid: 3b48678b-e7b8-4eda-bb46-b5d34dcf7817
ms.openlocfilehash: 9620706e6ac477246ce323a7fc3624291bb1dd6b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180194"
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>使用 dllexport 和 dllimport 定义内联 C++ 函数

**Microsoft 专用**

可以将函数定义为内联，并将函数与**dllexport**特性结合使用。 在这种情况下，将始终实例化并导出该函数，无论程序中是否有模块引用该函数。 假定该函数由另一个程序导入。

还可以定义为将声明的函数与 dllimport 特性内联。 在这种情况下，该函数可以展开（遵从 /Ob 规范），但决不实例化。 具体而言，如果采用内联导入函数的地址，则返回驻留在 DLL 中的函数地址。 此行为与采用非内联导入函数的地址相同。

这些规则适用于其定义出现在类定义中的内联函数。 此外，内联函数中的静态本地数据和字符串在 DLL 和客户端之间保持的标识与它们在单一程序（即，没有 DLL 接口的可执行文件）中保持的一样。

在提供导入的内联函数时谨慎操作。 例如，如果更新 DLL，请不要假定该客户端将使用更改后的 DLL 版本。 若要确保加载 DLL 的适当版本，请重新生成 DLL 的客户端。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[dllexport、dllimport](../cpp/dllexport-dllimport.md)
