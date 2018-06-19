---
title: vi_progid |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.vi_progid
dev_langs:
- C++
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 687a8a70d7f0a5381160a6515c80f6940cc0a434
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891280"
---
# <a name="viprogid"></a>vi_progid
指定独立于版本的窗体的 ProgID。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ vi_progid(  
   name  
) ];  
```  
  
#### <a name="parameters"></a>参数  
 *name*  
 表示的对象独立于版本的 ProgID。  
  
 Progid 提供用于标识 COM/ActiveX 对象的类标识符 (CLSID) 的用户可读的版本。  
  
## <a name="remarks"></a>备注  
 **Vi_progid** c + + 属性允许您指定的 COM 对象独立于版本的 ProgID。 ProgID 形式具有窗体*name1.name2.version*。 独立于版本的 ProgID 没有*版本*。 可以同时指定两个**progid**和**vi_progid**为组件类的属性。 如果不指定**vi_progid**，独立于版本的 ProgID 是指定的值[progid](../windows/progid.md)属性。  
  
 **vi_progid**意味着**组件类**特性，也就是说，如果你指定**vi_progid**，它是与指定的相同步**组件类**和**vi_progid**属性。  
  
 **Vi_progid**属性将导致一个类，以指定的名称下自动注册。 生成的.idl 文件将不显示 ProgID 的值。  
  
 在 ATL 项目中，如果[组件类](../windows/coclass.md)属性也存在，使用指定的 ProgID **GetVersionIndependentProgID**函数 (由插入**组件类**属性）。  
  
## <a name="example"></a>示例  
 请参阅[组件类](../windows/coclass.md)更大的示例的示例使用**vi_progid**。  
  
## <a name="requirements"></a>要求  
  
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
 [Typedef、 Enum、 Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [类特性](../windows/class-attributes.md)   
 [ProgID 密钥](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
