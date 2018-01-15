---
title: "线程处理 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.threading
dev_langs: C++
helpviewer_keywords: threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e44fec96391fff6700ecf4a453d7455bd75e9df7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="threading-c"></a>threading (C++)
指定 COM 对象的线程模型。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ threading(  
   model=enumeration  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 ***模型***（可选）  
 以下的线程处理模型之一：  
  
-   **单元**（单元线程处理）  
  
-   **非特定**（不带用户界面的.NET Framework 组件）  
  
-   **单个**（简单线程）  
  
-   **免费**（自由线程处理）  
  
-   **同时**（单元和自由线程处理）  
  
 默认值是**单元**。  
  
## <a name="remarks"></a>备注  
 **线程处理**c + + 特性在生成的.idl 文件中不显示，但会使用 COM 对象的实现中。  
  
 在 ATL 项目中，如果[组件类](../windows/coclass.md)属性也是存在，由指定的线程模型*模型*作为模板参数传递[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)类由插入**组件类**属性。  
  
 **线程处理**属性还可防止对访问[event_source](../windows/event-source.md)。  
  
## <a name="example"></a>示例  
 请参阅[许可](../windows/licensed.md)更大的示例的示例使用**线程处理**。  
  
## <a name="requirements"></a>惠?  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**class**， `struct`|  
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
