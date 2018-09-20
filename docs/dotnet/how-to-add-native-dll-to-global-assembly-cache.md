---
title: 如何： 向全局程序集缓存添加本机 DLL |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 74b24b96b28d8c5805a075a5ac1eee41173fc427
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431991"
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