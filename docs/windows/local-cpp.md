---
title: 本地 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.local
dev_langs:
- C++
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ad1fb4dd281918b0d9ab3494c9a9f060468fc389
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018092"
---
# <a name="local-c"></a>local (C++)
接口标头中使用时，可以使用 MIDL 编译器作为标头生成器。 单个函数中使用时，将指定为其生成无存根 （stub） 的本地过程。  
  
## <a name="syntax"></a>语法  
  
```cpp  
[local]  
```  
  
## <a name="remarks"></a>备注  
 **本地**c + + 属性具有相同的功能[本地](http://msdn.microsoft.com/library/windows/desktop/aa367071)MIDL 特性。  
  
## <a name="example"></a>示例  
 请参阅[call_as](../windows/call-as.md)有关如何使用的示例**本地**。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**接口**，接口方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|`dispinterface`|  
  
 有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [接口特性](../windows/interface-attributes.md)   
 [方法特性](../windows/method-attributes.md)   
 [call_as](../windows/call-as.md)   