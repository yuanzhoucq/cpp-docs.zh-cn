---
title: "链接器工具错误 LNK1000 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1000"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1000"
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1000
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未知错误；参考文档中的技术支持选项  
  
 记录错误发生时的环境，尝试隔离问题并创建一个可复制的测试用例，然后与 `Microsoft Product Support Services` 联系。  有关如何调查和报道这些错误的更多信息，请参见[http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;134650](http://support.microsoft.com/default.aspx?scid=kb;en-us;134650).  
  
 如果将标准头文件（例如 dos.h）与自己的文件混合，则可能出现此错误。  请首先使用 `#include` 标准头文件，后面跟着自己的头文件。