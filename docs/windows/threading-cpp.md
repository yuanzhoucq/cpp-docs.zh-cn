---
title: 线程处理 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.threading
dev_langs:
- C++
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e0e8b13a74c5b232e2662f80fc1cc8f80a1ffc9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652996"
---
# <a name="threading-c"></a>threading (C++)
指定 COM 对象的线程处理模型。  
  
## <a name="syntax"></a>语法  
  
```  
[ threading(  
   model=enumeration  
) ]  
```  
  
### <a name="parameters"></a>参数  
 *模型*（可选）  
 以下线程处理模型之一：  
  
-   `apartment` （单元线程处理）  
  
-   `neutral` （不带用户界面的.NET framework 组件）  
  
-   `single` （简单线程处理）  
  
-   `free` （自由线程处理）  
  
-   `both` （单元和自由线程处理）  
  
 默认值为 `apartment`。  
  
## <a name="remarks"></a>备注  
 **线程**c + + 属性生成的.idl 文件中未显示，但将在 COM 对象的实现中使用。  
  
 在 ATL 项目中，如果[组件类](../windows/coclass.md)属性也是存在，由指定的线程模型*模型*传递作为模板参数[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)类由插入`coclass`属性。  
  
 **线程**属性还能访问[event_source](../windows/event-source.md)。  
  
## <a name="example"></a>示例  
 请参阅[许可](../windows/licensed.md)的示例使用的示例**线程**。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**，**结构**|  
|**可重复**|否|  
|**必需的特性**|**coclass**|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [COM 特性](../windows/com-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [类特性](../windows/class-attributes.md)   
 [针对旧代码 （Visual c + +） 的多线程处理支持](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [非特定单元](http://msdn.microsoft.com/library/windows/desktop/ms681813)   