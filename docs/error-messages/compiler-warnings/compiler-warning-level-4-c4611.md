---
title: 编译器警告 （等级 4） C4611 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4611
dev_langs:
- C++
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5946c10b5e0e0e7e08f1ee37c77120896937adb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4611"></a>编译器警告（等级 4）C4611
function 和 c + + 对象析构之间的交互是不可移植  
  
 在某些平台上，包含的函数。**捕获**可能不支持 c + + 对象语义超出范围时销毁。  
  
 若要避免意外的行为，避免使用**捕获**具有构造函数和析构函数的函数中。  
  
 此警告时，才发出一次;请参阅[杂注警告](../../preprocessor/warning.md)。