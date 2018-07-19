---
title: 错误 C1092 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1092
dev_langs:
- C++
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8f5b5d903fe1fb2d3182a7b08f7bf82ddf334fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199244"
---
# <a name="fatal-error-c1092"></a>错误 C1092
“编辑并继续”不支持对数据类型的更改；需要生成  
  
 更改或自上次成功生成以来添加的数据类型。  
  
-   编辑并继续不支持对现有的数据类型，包括类、 结构或枚举定义的更改。 你必须停止调试并生成应用程序。  
  
-   编辑并继续不支持添加新的数据类型，如果程序数据库文件，如 vc*x*0 pdb (其中*x*是在使用 Visual c + + 的主要版本) 是只读的。 若要添加的数据类型，编译器必须在写入模式下打开.pdb 文件。  
  
### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>若要删除此错误，而无需结束当前调试会话  
  
1.  将数据类型改回其在发生错误前的状态。  
  
2.  在“调试”  菜单中选择“应用代码更改” 。  
  
### <a name="to-remove-this-error-without-changing-your-source-code"></a>若要在不更改源代码的情况下删除此错误  
  
1.  在“调试”  菜单上，选择“停止调试” 。  
  
2.  在“生成”  菜单上，选择“生成” 。  
  
 有关详细信息，请参阅 [受支持的代码更改](/visualstudio/debugger/supported-code-changes-cpp)。