---
title: "COM + 1.0，ATL COM + 1.0 组件向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.options
dev_langs:
- C++
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 36295e5ce296ea6ba982c4ce8cf729bf45860883
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0，ATL COM+ 1.0 组件向导
使用 ATL COM + 1.0 组件向导的此页可指定要支持的接口类型和其他接口。  
  
 ATL 项目和 ATL COM 类的详细信息，请参阅[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)。  
  
 **接口**  
 指示该对象支持的接口的类型。 默认情况下，该对象支持双重接口。  
  
|选项|说明|  
|------------|-----------------|  
|**双**|指定对象支持双重接口 (其 vtable 具有自定义接口函数和后期绑定`IDispatch`方法)。 允许 COM 客户端和自动化控制器都能访问该对象。|  
|**自定义**|指定对象支持自定义接口 （其 vtable 具有自定义接口函数）。 自定义接口可以比要快双重接口，尤其是跨进程边界。<br /><br /> -   **自动化兼容**将自动化的支持添加到自定义接口。 特性化项目中，将设置**oleautomation**组件类中的属性。|  
  
 **Queueable**  
 指示客户端可以调用使用消息队列以异步方式此组件。 将组件特性化宏自定义 (TLBATTR_QUEUEABLE，0) 添加到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目）。  
  
 **支持**  
 指示对错误处理和对象控制的附加支持。  
  
|选项|说明|  
|------------|-----------------|  
|**ISupportErrorInfo**|创建支持[ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md)接口以便对象可以返回到客户端的错误的信息。|  
|**IObjectControl**|提供对三个对象的访问[IObjectControl](http://msdn.microsoft.com/library/windows/desktop/ms686474)方法︰[激活](http://msdn.microsoft.com/library/windows/desktop/ms681303)， [CanBePooled](http://msdn.microsoft.com/library/windows/desktop/ms684322)，和[停用](http://msdn.microsoft.com/library/windows/desktop/ms687094)。|  
|**IObjectConstruct**|创建支持[IObjectConstruct](http://msdn.microsoft.com/library/windows/desktop/ms680583)界面，可从其他方法或对象的参数中传递管理。|  
  
 **事务**  
 指示该对象支持事务。 .Idl 文件 （非特性化项目） 中包括文件 mtxattr.h。  
  
|选项|说明|  
|------------|-----------------|  
|**支持**|指定该对象是永远不会事务流的根通过添加组件属性的宏 custom(TLBATTR_TRANS_SUPPORTED,0) 到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目）。|  
|**必需**|指定该对象可能会或可能不在事务流的根添加组件属性的宏 custom(TLBATTR_TRANS_REQUIRED,0) 到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目）。|  
|**不支持**|指定对象排除事务。 将组件属性的宏 custom(TLBATTR_TRANS_NOTSUPP,0) 添加到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目）。|  
|**新要求**|指定该对象是始终事务流的根通过添加组件属性的宏 custom(TLBATTR_TRANS_REQNEW,0) 到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目）。|  
  
## <a name="see-also"></a>另请参阅  
 [ATL COM + 1.0 组件向导](../../atl/reference/atl-com-plus-1-0-component-wizard.md)   
 [ATL COM + 1.0 组件](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)


