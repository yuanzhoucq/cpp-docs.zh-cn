---
title: "CAtlFileMapping 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CAtlFileMapping<T>
- ATL.CAtlFileMapping
- ATL::CAtlFileMapping
- CAtlFileMapping
- ATL.CAtlFileMapping<T>
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 2693647af904eab1ed0f84bc406bc1207d4a9b8c
ms.lasthandoff: 02/24/2017

---
# <a name="catlfilemapping-class"></a>CAtlFileMapping 类
此类表示内存映射文件，将强制转换运算符添加到的方法[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <typename T = char>  
class CAtlFileMapping : public CAtlFileMappingBase
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 用于强制转换运算符的数据的类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlFileMapping::operator T *](#operator_t_star)|允许隐式转换`CAtlFileMapping`对象添加到`T` ** \* **。|  
  
## <a name="remarks"></a>备注  
 此类会添加一个单一的强制转换运算符，以允许隐式转换`CAtlFileMapping`对象添加到`T` ** \* **。 由基类，提供其他成员[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)  
  
 `CAtlFileMapping`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlfile.h  
  
##  <a name="a-nameoperatortstara--catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFileMapping::operator T *  
 允许隐式转换`CAtlFileMapping`对象添加到`T` ** \* **。  
  
```  
operator T*() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回`T` ** \* **到内存映射文件的起始位置的指针。  
  
### <a name="remarks"></a>备注  
 调用[CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata)重新解释为返回的指针和`T` ** \* **其中*T*是用作此类的模板参数的类型。  
  
## <a name="see-also"></a>另请参阅  
 [CAtlFileMappingBase 类](../../atl/reference/catlfilemappingbase-class.md)   
 [类概述](../../atl/atl-class-overview.md)

