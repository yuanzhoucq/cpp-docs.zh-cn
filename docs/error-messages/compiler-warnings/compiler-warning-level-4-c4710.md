---
title: "编译器警告 （等级 4） C4710 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4710
dev_langs: C++
helpviewer_keywords: C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0464d924c21a029a97a8f03d30f88127f3aea6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4710"></a>编译器警告（等级 4）C4710
function： 函数未内联  
  
 为内联展开选定了给定的函数，但编译器没有执行内联。  
  
 在由编译器自行执行内联。 **内联**关键字、 like**注册**关键字，用作编译器提示。 编译器使用试探法来确定是否应该特定函数可对速度、 编译时加速代码进行内联，或它应使代码更小，编译的空间时特定函数进行内联。 编译的空间时，编译器将唯一内联非常小的函数。  
  
 在某些情况下，编译器将会机械原因而不内联某个特定的函数。 请参阅[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)有关编译器可能不内联函数的原因的列表。  
  
 默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。