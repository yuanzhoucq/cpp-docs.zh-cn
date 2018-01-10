---
title: "本地 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.local
dev_langs: C++
helpviewer_keywords: local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3543adfe0cb25f7946e6ed6c81c4bd66a7b60324
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="local-c"></a>local (C++)
接口标头中使用时，可以使用作为标头生成器的 MIDL 编译器。 当使用单个函数中，指定为其生成没有存根 （stub） 的本地过程。  
  
## <a name="syntax"></a>语法  
  
```  
  
[local]  
  
```  
  
## <a name="remarks"></a>备注  
 `local` C + + 属性具有相同的功能[本地](http://msdn.microsoft.com/library/windows/desktop/aa367071)MIDL 特性。  
  
## <a name="example"></a>示例  
 请参阅[call_as](../windows/call-as.md)以举例说明如何使用`local`。  
  
## <a name="requirements"></a>惠?  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|`interface`接口方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|**dispinterface**|  
  
 有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [接口特性](../windows/interface-attributes.md)   
 [方法特性](../windows/method-attributes.md)   
 [call_as](../windows/call-as.md)   
