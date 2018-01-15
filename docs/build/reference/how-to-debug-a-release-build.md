---
title: "如何： 调试发行版本 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 31113d9a5935536ac10b22c7b5f5af27b0d29970
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-debug-a-release-build"></a>如何：调试发行版本
你可以调试应用程序的发布版本。  
  
### <a name="to-debug-a-release-build"></a>若要调试的发布版本  
  
1.  打开**属性页**项目对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**C/c + +**节点。 设置**调试信息格式**到[C7 兼容 (/ Z7)](../../build/reference/z7-zi-zi-debug-information-format.md)或**程序数据库 (/Zi)**。  
  
3.  展开**链接器**单击**常规**节点。 设置**启用增量链接**到[否 (/ /INCREMENTAL: NO)](../../build/reference/incremental-link-incrementally.md)。  
  
4.  选择**调试**节点。 设置**生成调试信息**到[是 (/debug)](../../build/reference/debug-generate-debug-info.md)。  
  
5.  选择**优化**节点。 设置**引用**到[/opt: ref](../../build/reference/opt-optimizations.md)和**启用 COMDAT 折叠**到[/opt: icf](../../build/reference/opt-optimizations.md)。  
  
6.  现在，你可以调试版本生成应用程序。 若要发现问题，单步调试代码 （或使用在实时调试），直到你找到其中发生故障，并确定参数不正确或代码。  
  
     如果应用程序在调试版本中，正常运行，但在发布版本中失败，编译器优化措施之一可能会公开的源代码中有缺陷。 若要找出问题，请禁用为每个源代码文件选择的优化，直到你找到该文件，并且导致问题的优化。 （要加快该过程，你可以将文件分为两个组，禁用优化的一个组，并在组中，找到问题后继续除以直到隔离问题文件。）  
  
     你可以使用[/RTC](../../build/reference/rtc-run-time-error-checks.md)尝试公开您的调试版本中的此类 bug。  
  
     有关详细信息，请参阅[优化您的代码](../../build/reference/optimizing-your-code.md)。  
  
## <a name="see-also"></a>请参阅  
 [修复发行版本问题](../../build/reference/fixing-release-build-problems.md)