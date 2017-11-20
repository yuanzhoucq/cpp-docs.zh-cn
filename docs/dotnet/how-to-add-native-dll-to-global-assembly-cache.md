---
title: "如何： 将本机 DLL 添加到全局程序集缓存 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ef839617e80c668cd74458c397085b1166fdd70c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>如何：向全局程序集缓存添加本机 DLL
你可以将本机 DLL (而不是 COM) 放到全局程序集缓存中。  
  
## <a name="example"></a>示例  
 **/ASSEMBLYLINKRESOURCE** ，您可以在程序集中嵌入的本机 DLL。  
  
 有关详细信息，请参阅 [/ASSEMBLYLINKRESOURCE（链接到 .NET Framework 资源）](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)。  
  
```  
/ASSEMBLYLINKRESOURCE:MyComponent.dll  
```  
  
## <a name="see-also"></a>另请参阅  
 [使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)