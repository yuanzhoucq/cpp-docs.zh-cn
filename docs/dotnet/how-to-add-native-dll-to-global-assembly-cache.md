---
title: 如何： 将本机 DLL 添加到全局程序集缓存 |Microsoft 文档
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
ms.openlocfilehash: b7363de172eabc664bcde1e3bf42f8cc499e4251
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>如何：向全局程序集缓存添加本机 DLL
你可以将本机 DLL (而不是 COM) 放到全局程序集缓存中。  
  
## <a name="example"></a>示例  
 **/ASSEMBLYLINKRESOURCE** ，您可以在程序集中嵌入的本机 DLL。  
  
 有关详细信息，请参阅 [/ASSEMBLYLINKRESOURCE（链接到 .NET Framework 资源）](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)。  
  
```  
/ASSEMBLYLINKRESOURCE:MyComponent.dll  
```  
  
## <a name="see-also"></a>请参阅  
 [使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)