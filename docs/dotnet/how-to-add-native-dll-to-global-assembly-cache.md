---
title: 如何：向全局程序集缓存添加本机 DLL
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
ms.openlocfilehash: 1b11ebfae704ca1529113a00b463df728c85fe60
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641358"
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>如何：向全局程序集缓存添加本机 DLL

可以将本机 DLL (而不是 COM) 放入全局程序集缓存中。

## <a name="example"></a>示例

**/ASSEMBLYLINKRESOURCE**允许您在程序集中嵌入的本机 DLL。

有关详细信息，请参阅 [/ASSEMBLYLINKRESOURCE（链接到 .NET Framework 资源）](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)。

```
/ASSEMBLYLINKRESOURCE:MyComponent.dll
```

## <a name="see-also"></a>请参阅

[使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)