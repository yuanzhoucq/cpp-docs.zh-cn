---
title: "编译器警告 （等级 1） C4655 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4655
dev_langs:
- C++
helpviewer_keywords:
- C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: 058086bb4617f59f53de706b38477bd868e297d3
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4655"></a>编译器警告（等级 1）C4655
**'**   
 ***符号*': 自上次生成以来的新增功能，变量类型或以不同的方式在其他位置定义**  
  
 自上次成功生成后你更改或添加了新的数据类型。 “编辑并继续”不支持对现有数据类型的更改。  
  
 此警告后跟[错误 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)。 有关详细信息，请参阅[支持的代码更改](/visualstudio/debugger/supported-code-changes-cpp)。  
  
### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>若要在不结束当前调试会话的情况下删除此警告  
  
1.  将数据类型改回其在发生错误前的状态。  
  
2.  在“调试”  菜单中选择“应用代码更改” 。  
  
### <a name="to-remove-this-warning-without-changing-your-source-code"></a>若要在不更改源代码的情况下删除此警告  
  
1.  在“调试”  菜单上，选择“停止调试” 。  
  
2.  在“生成”  菜单上，选择“生成” 。
