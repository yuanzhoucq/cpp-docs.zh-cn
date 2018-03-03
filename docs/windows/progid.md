---
title: "progid |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.progid
dev_langs:
- C++
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 862629af7e279cf1f03a5e9adc9424b330ee1d90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="progid"></a>progid
指定 COM 对象的 ProgID。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ progid(  
   name  
) ];  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
 表示的对象的 ProgID。  
  
 Progid 提供用于标识 COM/ActiveX 对象的类标识符 (CLSID) 的用户可读的版本。  
  
## <a name="remarks"></a>备注  
 **Progid** c + + 属性允许您指定的 COM 对象的 ProgID。 ProgID 形式具有窗体*name1.name2.version*。 如果不指定*版本*对于其 ProgID 的默认版本为 1。 如果不指定*name1.name2*，默认名称是*classname.classname*。 如果不指定**progid**而且你指定**vi_progid**， *name1.name2* ，将从**vi_progid**和 (下一步顺序追加数字） 版本。  
  
 如果使用的属性块**progid**也不使用`uuid`，编译器将检查注册表以查看是否`uuid`指定存在**progid**。 如果**progid**未指定，则将使用版本 （和组件类名称，如果创建组件类） 来生成**progid**。  
  
 **progid**意味着**组件类**特性，也就是说，如果你指定**progid**，它是与指定的相同步**组件类**和**progid**属性。  
  
 **Progid**属性将导致一个类，以指定的名称下自动注册。 生成的.idl 文件将不会显示**progid**值。  
  
 当使用 ATL 项目中使用此属性时，该属性的行为更改。 除了上述行为，指定与此属性的信息用于**GetProgID**函数，通过插入**组件类**属性。 有关详细信息，请参阅[组件类](../windows/coclass.md)属性。  
  
## <a name="example"></a>示例  
 请参阅示例[组件类](../windows/coclass.md)的示例使用**progid**。  
  
## <a name="requirements"></a>惠?  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**class**， `struct`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [类特性](../windows/class-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [ProgID 密钥](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
