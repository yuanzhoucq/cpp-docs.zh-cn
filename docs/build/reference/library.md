---
title: "LIBRARY | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LIBRARY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LIBRARY .def 文件语句"
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LIBRARY
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

告知 LINK 创建 DLL。  LINK 同时还创建导入库，除非生成中使用了 .exp 文件。  
  
```  
LIBRARY [library][BASE=address]  
```  
  
## 备注  
 *library* 参数指定 DLL 的名称。  也可以使用 [\/OUT](../../build/reference/out-output-file-name.md) 链接器选项指定 DLL 输出名。  
  
 BASE\=*address* 参数设置操作系统用来加载 DLL 的基址。  该参数重写 0x10000000 的默认 DLL 位置。  有关基址的详细信息，请参见 [\/BASE](../../build/reference/base-base-address.md) 选项说明。  
  
 请记住，在生成 DLL 时使用 [\/DLL](../../build/reference/dll-build-a-dll.md) 链接器选项。  
  
## 请参阅  
 [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)