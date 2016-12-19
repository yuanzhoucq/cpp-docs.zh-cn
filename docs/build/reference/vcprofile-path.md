---
title: "VCPROFILE_PATH | Microsoft Docs"
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
  - "VCPROFILE_PATH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VCPROFILE_PATH 环境变量"
ms.assetid: 25217aa4-7e86-4eba-854d-10b3c457e4df
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# VCPROFILE_PATH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定创建 .pgc 文件的目录。  
  
## 语法  
  
```  
VCPROFILE_PATH=path  
```  
  
#### 参数  
 `path`  
 将 .pgc 文件添加到的目录路径。  
  
## 备注  
 默认情况下，在配置二进制文件所处的相同目录下创建 .pgc 文件。但是，如果二进制文件的绝对路径不存在（例如，如果在生成二进制文件的计算机以外的其他计算机上运行配置方案，就可能出现这种情况），可以将 `VCPROFILE_PATH` 设置为现存的路径。  
  
## 示例  
  
```  
set VCPROFILE_PATH=c:\  
```  
  
## 请参阅  
 [用于按配置文件优化的环境变量](../../build/reference/environment-variables-for-profile-guided-optimizations.md)