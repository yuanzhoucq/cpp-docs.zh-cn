---
title: "如何：调试发行版本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "调试 [C++], 发行版本"
  - "发行版本, 调试"
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 如何：调试发行版本
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以调试应用程序的发布版本。  
  
### 调试发布版本  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**“C\/C\+\+”**节点。  将**“调试信息格式”**设置为 [C7 兼容\(\/Z7\)](../../build/reference/z7-zi-zi-debug-information-format.md) 或**“程序数据库\(\/Zi\)”**。  
  
3.  展开**“链接器”**并单击**“常规”**节点。  将**“启用增量链接”**设置为[否\(\/INCREMENTAL:NO\)](../../build/reference/incremental-link-incrementally.md)。  
  
4.  选择**“调试”**节点。  将**“生成调试信息”**设置为[是\(\/DEBUG\)](../../build/reference/debug-generate-debug-info.md)。  
  
5.  选择**“优化”**节点。  将**“引用”**设置为 [\/OPT:REF](../../build/reference/opt-optimizations.md)，将**“启用 COMDAT 折叠”**设置为 [\/OPT:ICF](../../build/reference/opt-optimizations.md)。  
  
6.  现在可以调试应用程序的发布版本了。  若要找到问题，请逐句通过代码（或者使用实时调试），直到找到发生失败的位置，然后确定不正确的参数或代码。  
  
     如果应用程序在调试版本中正常运行，但在发布版本中运行失败，则可能是某个编译器优化在源代码中发现了缺陷。  若要找出该问题，应禁用为每个源代码文件选择的优化，直到您找到该文件和导致该问题的优化为止。（若要加快此过程，您可以将文件划分为两组，对一组禁用优化，在组中发现问题时，继续划分直到您找到问题文件为止。）  
  
     您可以使用 [\/RTC](../../build/reference/rtc-run-time-error-checks.md) 以尝试在您的调试版本中暴露这样的 bug。  
  
     有关详细信息，请参阅[优化代码](../../build/reference/optimizing-your-code.md)。  
  
## 请参阅  
 [修复发行版本问题](../../build/reference/fixing-release-build-problems.md)