---
title: "未能找到标准库：“&lt;文件名&gt;” | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40049"
  - "bc40049"
helpviewer_keywords: 
  - "BC40049"
ms.assetid: a292f97e-4852-4021-b300-7ab47beb95d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 未能找到标准库：“&lt;文件名&gt;”
[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 无法找到或打开编译和链接其中一个所需的标准 DLL 库。  
  
 无法使用的库是最有可能是 mscorlib.dll 或 microsoft.visualbasic.dll。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的信息，请参见 [在 Visual Basic 中配置警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **错误 ID：**BC40049  
  
### 更正此错误  
  
1.  验证错误消息中提到的文件是否存在于正在运行 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 的硬盘上。 通常情况下标准库应驻留在 \\WINNT\\Microsoft.NET\\Framework 或 \\WINDOWS\\Microsoft.NET\\Framework 下的子目录中。  
  
2.  验证文件和目录都不具有阻止 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 的读取访问权限的设置或特性。  
  
3.  验证文件名和扩展名拼写是否正确。 大小写并不是问题。  
  
4.  如果文件似乎处于正确的位置而且可以访问，它可能在磁盘上已损坏。 如有可能，重新安装 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)]。  
  
5.  请注明确切的文件名和扩展名，然后与 Microsoft 产品支持服务联系。  
  
## 请参阅  
 [从命令行生成](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)   
 [如何：调用命令行编译器](../Topic/How%20to:%20Invoke%20the%20Command-Line%20Compiler%20\(Visual%20Basic\).md)   
 [与我们交流](../Topic/Talk%20to%20Us.md)