---
title: "常规语言更改 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 79a70768-225c-4ae2-84d1-178b20a9b042
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 87ff7f55b67c4e8a84d15099432962ee0939d13a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="general-language-changes-ccli"></a>常规语言更改 (C++/CLI)
大量的托管扩展中更改 c + + 为 Visual c + + CLR 语言功能。  
  
 在本部分中所述的更改是一种语言杂注。 它包括某项更改的字符串文本，省略号之间的重载决策中的更改的处理和`Param`属性，更改`typeof`到`typeid`，构造函数初始值设定项列表的调用中的更改和新的强制转换表示法，引入的`safe_cast`。  
  
 [字符串文本](../dotnet/string-literal.md)  
 讨论的字符串文本处理的更改方式。  
  
 [参数数组和省略号](../dotnet/param-array-and-ellipsis.md)  
 讨论如何`ParamArray`现在优先于旁边的省略号 (`...`) 用于解决具有不同数目的参数的函数调用。  
  
 [typeof 转到 T::typeid](../dotnet/typeof-goes-to-t-typeid.md)  
 讨论如何`typeof`运算符由`typeid`。  
  
 [初始值设定项列表](../dotnet/initializer-lists.md)  
 讨论了初始值设定项列表的调用顺序中的更改。  
  
 [强制转换表示法和 safe_cast<> 介绍](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)  
 讨论引入的更改的强制转换表示法，并且在特定`safe_cast`。  
  
## <a name="see-also"></a>请参阅  
 [C++/CLI 迁移入门](../dotnet/cpp-cli-migration-primer.md)