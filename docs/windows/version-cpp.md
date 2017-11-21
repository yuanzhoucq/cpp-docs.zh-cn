---
title: "版本 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.version
dev_langs: C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 757ab7a6d2c8b846a51da359c4b8dc5a72c6e9e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="version-c"></a>version (C++)
标识的类的多个版本之间的特定版本。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ version(  
   "version"  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *version*  
 组件类的版本号。 如果未指定，1.0 将放置在.idl 文件中。  
  
## <a name="remarks"></a>备注  
 **版本**c + + 属性具有相同的功能[版本](http://msdn.microsoft.com/library/windows/desktop/aa367306)MIDL 特性，传递到生成的.idl 文件。  
  
## <a name="example"></a>示例  
 请参阅[可绑定](../windows/bindable.md)更大的示例的示例使用**版本**。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**class**， `struct`|  
|**可重复**|No|  
|**必需的特性**|**coclass**|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另请参阅  
 [编译器特性](../windows/compiler-attributes.md)   
 [类特性](../windows/class-attributes.md)   
