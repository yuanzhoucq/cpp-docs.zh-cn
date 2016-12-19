---
title: "space_info 结构 | Microsoft Docs"
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
  - "filesystem/std::tr2::sys::space_info"
dev_langs: 
  - "C++"
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
caps.latest.revision: 13
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# space_info 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

保存有关卷的信息。  
  
## 语法  
  
```  
struct space_info;  
```  
  
## 成员  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|`unsigned long long available`|表示可用于表示卷上数据的字节数。|  
|`unsigned long long capacity`|表示卷可以表示的字节总数。|  
|`unsigned long long free`|表示不用于表示卷上数据的字节数。|  
  
## 要求  
 **标头：**filesystem  
  
 **命名空间：**std::tr2::sys  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem\>](../standard-library/filesystem.md)   
 [space 函数](http://msdn.microsoft.com/zh-cn/7fce0b0e-523b-4598-b218-47245d0204ca)   
 [文件系统导航 \(C\+\+\)](../standard-library/file-system-navigation.md)