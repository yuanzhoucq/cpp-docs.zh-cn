---
title: progid |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.progid
dev_langs:
- C++
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 98057773d6cbb51fe5aacc3ac814af89532bd887
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607980"
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
  
 Progid 提供用来标识 COM/ActiveX 对象的类标识符 (CLSID) 的用户可读版本。  
  
## <a name="remarks"></a>备注  
 **Progid** c + + 属性允许您指定 COM 对象的 ProgID。 ProgID 具有窗体*name1.name2.version*。 如果未指定*版本*ProgID 的默认版本为 1。 如果未指定*name1.name2*，默认名称是*classname.classname*。 如果未指定**progid**并且你指定`vi_progid`， *name1.name2*取自`vi_progid`和 （下一个序列号） 追加版本。  
  
 如果使用的特性块**progid**还使用**uuid**，编译器将检查注册表以查看是否**uuid**存在指定**progid**. 如果**progid**未指定，则将使用的版本 （和组件类名称，如果创建组件类） 来生成**progid**。  
  
 **progid**意味着`coclass`属性，也就是说，如果您指定**progid**，它是与指定相同的功能`coclass`并**progid**属性。  
  
 **Progid**属性会导致自动注册的指定名称的类。 生成的.idl 文件将不会显示**progid**值。  
  
 当使用 ATL 的项目中使用此属性时，该属性的行为更改。 除了上述行为，在使用用此特性指定的信息`GetProgID`函数，由注入`coclass`属性。 有关详细信息，请参阅[组件类](../windows/coclass.md)属性。  
  
## <a name="example"></a>示例  
 有关示例，请参阅[组件类](../windows/coclass.md)的示例使用**progid**。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**，**结构**|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [类特性](../windows/class-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [ProgID 密钥](http://msdn.microsoft.com/library/windows/desktop/dd542719)   