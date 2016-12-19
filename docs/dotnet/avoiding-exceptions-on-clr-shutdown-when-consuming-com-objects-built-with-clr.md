---
title: "使用以 /clr 生成的 COM 对象时避免 CLR 关闭异常 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 编译器选项 [C++], CLR 关闭异常"
  - "/clr 编译器选项 [C++], COM 对象"
  - "CLR 关闭异常 [C++]"
  - "互操作 [C++], CLR 关闭异常"
  - "互操作性 [C++], CLR 关闭异常"
  - "混合程序集 [C++], CLR 关闭异常"
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用以 /clr 生成的 COM 对象时避免 CLR 关闭异常
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

公共语言运行时 \(CLR\) 进入关闭模式后，本机函数会限制对 CLR 服务的访问。  当尝试调用使用 **\/clr** 编译的 COM 对象上的 Release 时，CLR 将转换为本机代码，然后转换回托管代码以为 IUnknown::Release 调用（它是在托管代码中定义的）提供服务。  由于该调用处于关闭模式，CLR 将阻止它返回到托管代码中。  
  
 若要解决此问题，请确保从 Release 方法调用的析构函数仅包含本机代码。  
  
## 请参阅  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)