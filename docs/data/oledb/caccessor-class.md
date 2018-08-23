---
title: CAccessor 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
dev_langs:
- C++
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9e7f722d4d1759bdec7a23bb15076b38de000eb6
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337412"
---
# <a name="caccessor-class"></a>CAccessor 类
表示一个访问器类型。  
  
## <a name="syntax"></a>语法  
  
```cpp
template <class T>  
class CAccessor : public CAccessorBase, public T  
```  
  
### <a name="parameters"></a>参数  
 *T*  
 用户记录类。  
  
## <a name="remarks"></a>备注  
 使用一条记录以静态方式绑定到数据源时。 该记录包含缓冲区。 此类支持多个访问器的行集。  
  
 当你知道的结构和数据库类型时，请使用此访问器类型。  
  
 如果您访问器包含指向内存的字段 (如`BSTR`或接口)，必须释放，调用成员函数[caccessorrowset:: Freerecordmemory](../../data/oledb/caccessorrowset-freerecordmemory.md)在下一步之前读取记录。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)