---
title: "IDL 特性，添加属性向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.prop.idlattributes
dev_langs: C++
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ec158c117161c5a5c2ffd23cef0d5c79c312ae7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="idl-attributes-add-property-wizard"></a>“添加属性向导”->“IDL 特性”
添加属性向导的此页用于指定属性的任何接口定义语言 (IDL) 设置。  
  
 **id**  
 设置标识的属性的数字 ID。 此选项不可用的属性的自定义的接口。 请参阅[id](http://msdn.microsoft.com/library/windows/desktop/aa367040)中*MIDL 引用*。  
  
 **helpcontext**  
 指定允许用户查看有关此帮助文件中的属性的信息的上下文 ID。 请参阅[helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851)中*MIDL 引用*。  
  
 **helpstring**  
 指定用于描述应用于元素的字符字符串。 默认情况下，它设置为"属性*属性名称*。" 请参阅[helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856)中*MIDL 引用*。  
  
## <a name="other-options"></a>其他选项  
 并非所有选项都都适用于所有属性类型。  
  
|选项|描述|  
|------------|-----------------|  
|**bindable**|指示属性支持数据绑定。 请参阅[可绑定](http://msdn.microsoft.com/library/windows/desktop/aa366738)中*MIDL 引用*。 对于该属性的常用实现，此选项默认设置，并且，则不可更改。|  
|**defaultbind**|指示这最佳的单个、 可绑定属性表示该对象。 请参阅[defaultbind](http://msdn.microsoft.com/library/windows/desktop/aa366790)中*MIDL 引用*。|  
|**displaybind**|指示此属性，应显示给用户作为可绑定。 请参阅[displaybind](http://msdn.microsoft.com/library/windows/desktop/aa366804)中*MIDL 引用*。|  
|**immediatebind**|指示数据库将立即收到通知的所有更改的数据绑定对象的此属性。 请参阅[immediatebind](http://msdn.microsoft.com/library/windows/desktop/aa367045)中*MIDL 引用*。|  
|**defaultcollelem**|指示该属性是默认集合的某个元素的访问器函数。 请参阅[defaultcollelem](http://msdn.microsoft.com/library/windows/desktop/aa366792)中*MIDL 引用*。|  
|**nonbrowsable**|标记的接口或调度接口的成员，不应在属性浏览器中显示。 请参阅[nonbrowsable](http://msdn.microsoft.com/library/windows/desktop/aa367117)中*MIDL 引用*。|  
|**requestedit**|该值指示属性是否支持**OnRequestEdit**通知，请参阅[requestedit](http://msdn.microsoft.com/library/windows/desktop/aa367155)中*MIDL 引用*。 对于该属性的常用实现，此选项默认设置，并且，则不可更改。|  
|**源**|指示属性的成员是事件的源。 请参阅[源](http://msdn.microsoft.com/library/windows/desktop/aa367166)中*MIDL 引用*。|  
|**hidden**|指示该属性存在，但不是应在面向用户的浏览器中显示。 请参阅[隐藏](http://msdn.microsoft.com/library/windows/desktop/aa366861)中*MIDL 引用*。|  
|**restricted**|指定该属性不能任意调用。 请参阅[受限](http://msdn.microsoft.com/library/windows/desktop/aa367157)中*MIDL 引用*。|  
|`local`|向 MIDL 编译器指定的属性不是远程的。 请参阅[本地](http://msdn.microsoft.com/library/windows/desktop/aa367071)中*MIDL 引用*。|  
  
## <a name="see-also"></a>请参阅  
 [添加属性](../ide/adding-a-property-visual-cpp.md)   
 [名称，添加属性向导](../ide/names-add-property-wizard.md)   
 [实现接口](../ide/implementing-an-interface-visual-cpp.md)   
 [常用属性](../ide/stock-properties.md)