---
title: “添加方法向导”->“IDL 特性”| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.method.idlattrib
dev_langs:
- C++
helpviewer_keywords:
- Add Method Wizard [C++]
- IDL attributes, Add Method Wizard
ms.assetid: f80c3bc1-b515-4d6c-83ee-98c2c21ba902
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a7a1e8fe89f64ad5909e7c1415545e3b3d80196
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337764"
---
# <a name="idl-attributes-add-method-wizard"></a>IDL 特性，添加方法向导
使用“添加方法向导”的此页为方法指定任何接口定义语言 (IDL) 设置。  
  
 **id**  
 设置标识方法的数字 ID。 请参阅 MIDL 引用中的 [ID](http://msdn.microsoft.com/library/windows/desktop/aa367040)。  
  
 此框不可用于自定义接口和 MFC 调度接口。  
  
 **call_as**  
 指定此本地方法可映射到的远程方法的名称。 请参阅 MIDL 引用中的 [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748)。  
  
 不可用于 MFC 调度接口。  
  
 **helpcontext**  
 指定一个上下文 ID，让用户可以在帮助文件中查看此方法的相关信息。 请参阅 MIDL 引用中的 [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851)。  
  
 不可用于 MFC 调度接口。  
  
 **helpstring**  
 指定一个字符串，用于描述应用该字符串的元素。 默认情况下，该字符串设置为“method Method name”。 请参阅 MIDL 引用中的 [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856)。  
  
 不可用于 MFC 调度接口。  
  
 **附加特性**  
 不可用于 MFC 调度接口。  
  
|特性|描述|  
|---------------|-----------------|  
|**hidden**|指示该方法虽然存在，但不应在面向用户的浏览器中显示。 请参阅 MIDL 引用中的 [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861)。|  
|**source**|指示方法的一个成员是事件源。 请参阅 MIDL 引用中的 [source](http://msdn.microsoft.com/library/windows/desktop/aa367166)。|  
|`local`|向 MIDL 编译器指出该方法不是远程的。 请参阅 MIDL 引用中的 [local](http://msdn.microsoft.com/library/windows/desktop/aa367071)。|  
|**restricted**|指定此方法不能任意调用。 请参阅 MIDL 引用中的 [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157)。|  
|**vararg**|指定方法采用的参数数目可变。 为了实现这一点，最后一个参数必须是包含所有剩余参数的 VARIANT 类型的安全数组。 请参阅 MIDL 引用中的 [vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304)。|  
  
## <a name="see-also"></a>请参阅  
 [添加方法](../ide/adding-a-method-visual-cpp.md)   
 [添加方法向导](../ide/add-method-wizard.md)