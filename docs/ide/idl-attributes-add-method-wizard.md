---
title: "IDL 特性，添加方法向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.method.idlattrib
dev_langs:
- C++
helpviewer_keywords:
- Add Method Wizard [C++]
- IDL attributes, Add Method Wizard
ms.assetid: f80c3bc1-b515-4d6c-83ee-98c2c21ba902
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9792f8b7758ff5a1e5742b6643d9f73931bce6f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="idl-attributes-add-method-wizard"></a>IDL 特性，添加方法向导
添加方法向导的此页用于指定的方法的任何接口定义语言 (IDL) 设置。  
  
 **id**  
 设置标识的方法的数值 ID。 请参阅[id](http://msdn.microsoft.com/library/windows/desktop/aa367040)中*MIDL 引用*。  
  
 此框不可用的自定义接口，并且不可用于 MFC 调度接口。  
  
 **call_as**  
 指定此本地方法可以映射到的远程方法的名称。 请参阅[call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748)中*MIDL 引用*。  
  
 对于 MFC 调度接口不可用。  
  
 **helpcontext**  
 指定允许用户查看有关此方法帮助文件中的信息的上下文 ID。 请参阅[helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851)中*MIDL 引用*。  
  
 对于 MFC 调度接口不可用。  
  
 **helpstring**  
 指定用于描述应用于元素的字符字符串。 默认情况下，它设置为"方法*方法名称*。" 请参阅[helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856)中*MIDL 引用*。  
  
 对于 MFC 调度接口不可用。  
  
 **其他属性**  
 对于 MFC 调度接口不可用。  
  
|特性|描述|  
|---------------|-----------------|  
|**hidden**|指示方法存在，但不是应在面向用户的浏览器中显示。 请参阅[隐藏](http://msdn.microsoft.com/library/windows/desktop/aa366861)中*MIDL 引用*。|  
|**源**|指示该方法的成员是事件的源。 请参阅[源](http://msdn.microsoft.com/library/windows/desktop/aa367166)中*MIDL 引用*。|  
|`local`|指定 MIDL 编译器此方法不是远程。 请参阅[本地](http://msdn.microsoft.com/library/windows/desktop/aa367071)中*MIDL 引用*。|  
|**restricted**|指定不能任意调用方法。 请参阅[受限](http://msdn.microsoft.com/library/windows/desktop/aa367157)中*MIDL 引用*。|  
|**vararg**|指定该方法采用数目可变的参数。 若要实现此目的，最后一个参数必须是安全数组的**VARIANT**包含所有剩余的自变量的类型。 请参阅[vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304)中*MIDL 引用*。|  
  
## <a name="see-also"></a>请参阅  
 [添加方法](../ide/adding-a-method-visual-cpp.md)   
 [添加方法向导](../ide/add-method-wizard.md)