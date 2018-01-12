---
title: "编译器警告 （等级 4） C4611 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4611
dev_langs: C++
helpviewer_keywords: C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3020cf7d115b735141b81e9007ac7fd027ed8674
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4611"></a>编译器警告（等级 4）C4611
function 和 c + + 对象析构之间的交互是不可移植  
  
 在某些平台上，包含的函数。**捕获**可能不支持 c + + 对象语义超出范围时销毁。  
  
 若要避免意外的行为，避免使用**捕获**具有构造函数和析构函数的函数中。  
  
 此警告时，才发出一次;请参阅[杂注警告](../../preprocessor/warning.md)。