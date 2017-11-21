---
title: "编译器警告 （等级 1） C4910 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f0402e03d77968de3b4c1addf58c481ec85a61b8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4910"></a>编译器警告（等级 1）C4910
\<标识符 >: __declspec （dllexport） 和 extern 不兼容的显式实例化上  
  
 名为的显式模板实例化*\<标识符 >*修改两个`__declspec(dllexport)`和`extern`关键字。 但是，这些关键字互斥。 `__declspec(dllexport)` 关键字表示实例化模板类，而 `extern` 关键字表示不要自动实例化模板类。  
  
## <a name="see-also"></a>另请参阅  
 [显式实例化](../../cpp/explicit-instantiation.md)   
 [dllexport、 dllimport](../../cpp/dllexport-dllimport.md)   
 [一般规则和限制](../../cpp/general-rules-and-limitations.md)