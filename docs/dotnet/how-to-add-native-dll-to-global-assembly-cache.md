---
title: "如何：向全局程序集缓存添加本机 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], 本机"
  - "GAC（全局程序集缓存）, 加载本机 DLL"
  - "本机 DLL [C++]"
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：向全局程序集缓存添加本机 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以将本机 DLL（不是 COM）放入全局程序集缓存中。  
  
## 示例  
 通过 **\/ASSEMBLYLINKRESOURCE** 可将本机 DLL 嵌入程序集中。  
  
 有关详细信息，请参阅[\/ASSEMBLYLINKRESOURCE（链接到 .NET Framework 资源）](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)。  
  
```  
/ASSEMBLYLINKRESOURCE:MyComponent.dll  
```  
  
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)