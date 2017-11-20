---
title: "range_adapter (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::range_adapter
dev_langs: C++
helpviewer_keywords: range_adapter class [STL/CLR]
ms.assetid: 3fbe2a65-1216-46a0-a182-422816b80cfb
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5455c1912b3108291f530ee9488a4e0078ba39a2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="rangeadapter-stlclr"></a>range_adapter (STL/CLR)
一种模板类，用于包装一对迭代器，用于实现多个基类库 (BCL) 接口。 Range_adapter 用于处理 STL/CLR 范围，就像它是 BCL 集合。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Iter>  
    ref class range_adapter  
        :   public  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<Value>,  
        System::Collections::Generic::ICollection<Value>  
    { ..... };  
```  
  
#### <a name="parameters"></a>参数  
 Iter  
 与已包装的迭代器关联的类型。  
  
## <a name="members"></a>成员  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[range_adapter::range_adapter (STL/CLR)](../dotnet/range-adapter-range-adapter-stl-clr.md)|将构造一个适配器对象。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[range_adapter::operator= (STL/CLR)](../dotnet/range-adapter-operator-assign-stl-clr.md)|替换存储的迭代器对。|  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:System.Collections.IEnumerable>|循环访问集合中的元素。|  
|<xref:System.Collections.ICollection>|维护一的组元素。|  
|<xref:System.Collections.Generic.IEnumerable%601>|循环访问集合中的类型化元素...|  
|<xref:System.Collections.Generic.ICollection%601>|维护一的组类型化的元素。|  
  
## <a name="remarks"></a>备注  
 Range_adapter 存储一对迭代器，反过来分隔的元素序列。 该对象实现四个 BCL 接口，可以循环访问的元素顺序。 使用此模板类来操作非常类似 BCL 容器 STL/CLR 范围。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/适配器 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)   
 [make_collection (STL/CLR)](../dotnet/make-collection-stl-clr.md)