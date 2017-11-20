---
title: "typeof 转到 t:: typeid |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- typeid operator
- __typeof keyword
- typeid keyword [C++]
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 90c75b67dc6496f51d335f83a49242b7f7ae0b29
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="typeof-goes-to-ttypeid"></a>typeof 转到 T::typeid
`typeof`由 c + + 托管扩展中使用的运算符`typeid`Visual c + + 中的关键字。  
  
 在托管扩展中，`__typeof()`运算符返回关联`Type*`对象时传递的托管类型的名称。 例如：  
  
```  
// Creates and initializes a new Array instance.  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 在新语法中，`__typeof`其他形式的已替换为`typeid`返回`Type^`时指定的托管的类型。  
  
```  
// Creates and initializes a new Array instance.  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
## <a name="see-also"></a>另请参阅  
 [常规语言更改 (C + + /cli CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [typeid](../windows/typeid-cpp-component-extensions.md)