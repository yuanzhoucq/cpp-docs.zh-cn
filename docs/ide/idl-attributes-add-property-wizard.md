---
title: IDL 特性，添加属性向导 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.prop.idlattributes
dev_langs:
- C++
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7da654321dfae520f458374654a21a9e8ebb98f5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706640"
---
# <a name="idl-attributes-add-property-wizard"></a>“添加属性向导”->“IDL 特性”
使用“添加属性向导”的此页面来指定属性的任何接口定义语言 (IDL) 设置。  
  
- **id**

   设置标识属性的数字 ID。 此选项不适用于自定义接口的属性。 请参阅 MIDL 引用中的 [ID](/windows/desktop/Midl/id)。  
  
- **helpcontext**

   指定一个上下文 ID，使用户在帮助文件中查看关于此属性的信息。 请参阅 MIDL 引用中的 [helpcontext](/windows/desktop/Midl/helpcontext)。  
  
- **helpstring**

   指定一个字符串，用于描述应用该字符串的元素。 默认情况下，它设置为“属性（属性名称）”。 请参阅 MIDL 引用中的 [helpstring](/windows/desktop/Midl/helpstring)。  
  
## <a name="other-options"></a>其他选项  

并非所有选项都适用于所有属性类型。  
  
|选项|描述|  
|------------|-----------------|  
|**bindable**|指示该属性支持数据绑定。 请参阅 MIDL 引用中的 [bindable](/windows/desktop/Midl/bindable)。 对于该属性的常用实现，此选项已默认设置，且不可更改。|  
|**defaultbind**|指示能够最好地表示该对象的单个可绑定属性。 请参阅 MIDL 引用中的 [defaultbind](/windows/desktop/Midl/defaultbind)。|  
|**displaybind**|指示应作为可绑定属性显示给用户的属性。 请参阅 MIDL 引用中的 [displaybind](/windows/desktop/Midl/displaybind)。|  
|**immediatebind**|指示将立即通知数据库对数据绑定对象的此属性所做的所有更改。 请参阅 MIDL 引用中的 [immediatebind](/windows/desktop/Midl/immediatebind)。|  
|**defaultcollelem**|指示该属性是默认集合的某个元素的访问器函数。 请参阅 MIDL 引用中的 [defaultcollelem](/windows/desktop/Midl/defaultcollelem)。|  
|**nonbrowsable**|标记不应显示在属性浏览器中的接口或调度接口成员。 请参阅 MIDL 引用中的 [nonbrowsable](/windows/desktop/Midl/nonbrowsable)。|  
|**requestedit**|指示该属性支持 OnRequestEdit 通知。请参阅 MIDL 引用中的 [requestedit](/windows/desktop/Midl/requestedit)。 对于该属性的常用实现，此选项已默认设置，且不可更改。|  
|**source**|指示该属性的成员是事件的源。 请参阅 MIDL 引用中的 [source](/windows/desktop/Midl/source)。|  
|**hidden**|指示该属性存在，但不应在面向用户的浏览器中显示。 请参阅 MIDL 引用中的 [hidden](/windows/desktop/Midl/hidden)。|  
|**restricted**|指定此属性不能任意调用。 请参阅 MIDL 引用中的 [restricted](/windows/desktop/Midl/restricted)。|  
|`local`|向 MIDL 编译器指出该属性不是远程的。 请参阅 MIDL 引用中的 [local](/windows/desktop/Midl/local)。|  
  
## <a name="see-also"></a>请参阅  
 [添加属性](../ide/adding-a-property-visual-cpp.md)   
 [名称，添加属性向导](../ide/names-add-property-wizard.md)   
 [实现接口](../ide/implementing-an-interface-visual-cpp.md)   
 [常用属性](../ide/stock-properties.md)