---
title: 参数数组和省略号 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function overloading, argument matching
ms.assetid: 492e3f6c-1c4c-4e0c-a358-72f2d39c30be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 20d13f327abe3e864007c4941af2ce9fd03ea05d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33158516"
---
# <a name="param-array-and-ellipsis"></a>参数数组和省略号
参数数组用于解析重载的函数调用的优先级已从托管扩展中的 c + + 更改为 Visual c + +。  
  
 在托管扩展和新语法中，没有显式支持对 C# 和 Visual Basic 支持的参数数组。 相反，标记所示普通数组具有一个属性，如下所示：  
  
```  
void Trace1( String* format, [ParamArray]Object* args[] );  
void Trace2( String* format, Object* args[] );  
```  
  
 虽然两者看起来相同，`ParamArray`特性将此标记用于 C# 或其他 CLR 语言作为元素随着每次调用具有可变数量的数组。 正在设置中的一个实例声明省略号重载函数的分辨率中的托管扩展和新的语法之间的程序行为的更改，第二个声明`ParamArray`属性，如提供的以下示例所示Artur Laksberg。  
  
```  
int fx(...); // 1  
int fx( [ParamArray] Int32[] ); // 2  
```  
  
 在托管扩展中，省略号的优先级高于是合理的因为该属性不是语言的正式方面的属性。 但是，在新语法中，直接在语言内, 现在支持的参数数组，并且它优先于省略号因为类型更强。 因此，在托管扩展中，调用  
  
```  
fx( 1, 2 );  
```  
  
 解析为`fx(...)`中新语法中，它解析为`ParamArray`实例。 上的程序行为取决于省略号实例的调用优先于可能性`ParamArray`，你将需要修改签名或调用。  
  
## <a name="see-also"></a>请参阅  
 [常规语言更改 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)