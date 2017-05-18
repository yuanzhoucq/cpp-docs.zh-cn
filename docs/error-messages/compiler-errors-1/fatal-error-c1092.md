---
title: "错误 C1092 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1092
dev_langs:
- C++
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: 6d93fd662b638126e21d5f5f034138c0e6f0e0ad
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="fatal-error-c1092"></a>错误 C1092
“编辑并继续”不支持对数据类型的更改；需要生成  
  
 您更改或添加自上次成功生成了数据类型。  
  
-   编辑并继续不支持对现有的数据类型，其中包括类、 结构或枚举定义的更改。 必须停止调试并生成该应用程序。  
  
-   编辑并继续不支持添加新的数据类型，如果程序数据库文件，如 vc*x*0.pdb (其中*x*是 Visual c + + 中使用的主要版本) 是只读的。 若要添加的数据类型，编译器必须在写模式下打开.pdb 文件。  
  
### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>若要删除此错误，而无需结束当前调试会话  
  
1.  将数据类型改回其在发生错误前的状态。  
  
2.  在“调试”  菜单中选择“应用代码更改” 。  
  
### <a name="to-remove-this-error-without-changing-your-source-code"></a>若要在不更改源代码的情况下删除此错误  
  
1.  在“调试”  菜单上，选择“停止调试” 。  
  
2.  在“生成”  菜单上，选择“生成” 。  
  
 有关详细信息，请参阅[支持的代码更改](/visualstudio/debugger/supported-code-changes-cpp)。
