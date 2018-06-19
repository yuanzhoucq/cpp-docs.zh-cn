---
title: CRowset 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CRowset<TAccessor>
- CRowset
- ATL::CRowset
- ATL::CRowset<TAccessor>
- ATL.CRowset
dev_langs:
- C++
helpviewer_keywords:
- CRowset class
ms.assetid: b0228a90-b8dd-47cc-b397-8d4c15c1e7f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5c9a23c2e879f0d2fe1add1a970c64f6fbcc27b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098571"
---
# <a name="crowset-class"></a>CRowset 类
封装 OLE DB 行集对象并在几个相关接口并提供行集数据的操作方法。  
  
## <a name="syntax"></a>语法

```cpp
template <class TAccessor = CAccessorBase>  
class CRowset  
```  
  
#### <a name="parameters"></a>参数  
 `TAccessor`  
 一个访问器类。 默认值为 `CAccessorBase`。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/crowset-addrefrows.md)|递增引用计数与当前行。|  
|[关闭](../../data/oledb/crowset-close.md)|释放行和当前`IRowset`接口。|  
|[Compare](../../data/oledb/crowset-compare.md)|比较两个书签使用[IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx)。|  
|[CRowset](../../data/oledb/crowset-crowset.md)|创建一个新`CRowset`对象并 （可选） 将其与关联**IRowset**作为参数提供的接口。|  
|[删除](../../data/oledb/crowset-delete.md)|删除行从行集使用[IRowsetChange:DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx)。|  
|[FindNextRow](../../data/oledb/crowset-findnextrow.md)|查找指定的书签之后的下一步的匹配行。|  
|[GetApproximatePosition](../../data/oledb/crowset-getapproximateposition.md)|返回对应于书签的行的近似位置。|  
|[GetData](../../data/oledb/crowset-getdata.md)|从行的行集的副本检索数据。|  
|[GetDataHere](../../data/oledb/crowset-getdatahere.md)|从指定的缓冲区中检索数据。|  
|[GetOriginalData](../../data/oledb/crowset-getoriginaldata.md)|检索最近从提取或传输到数据源，忽略挂起的更改的数据。|  
|[GetRowStatus](../../data/oledb/crowset-getrowstatus.md)|返回所有行的状态。|  
|[插入](../../data/oledb/crowset-insert.md)|创建并将插入新行使用[IRowsetChange:InsertRow](https://msdn.microsoft.com/en-us/library/ms716921.aspx)。|  
|[IsSameRow](../../data/oledb/crowset-issamerow.md)|将具有当前行的指定的行进行比较。|  
|[MoveFirst](../../data/oledb/crowset-movefirst.md)|将下一步提取位置重新定位到的初始位置。|  
|[MoveLast](../../data/oledb/crowset-movelast.md)|将移动到最后一个记录。|  
|[MoveNext](../../data/oledb/crowset-movenext.md)|从下一步的顺序行或指定的数量的下一行以外的位置提取数据。|  
|[MovePrev](../../data/oledb/crowset-moveprev.md)|移动到上一记录。|  
|[MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)|该书签从提取用书签标记的行或指定的偏移量处的行。|  
|[MoveToRatio](../../data/oledb/crowset-movetoratio.md)|提取行的行集中的小数部分位置 （从开始）。|  
|[ReleaseRows](../../data/oledb/crowset-releaserows.md)|调用[irowset:: Releaserows](https://msdn.microsoft.com/en-us/library/ms719771.aspx)释放当前的行句柄。|  
|[SetData](../../data/oledb/crowset-setdata.md)|设置中的行使用的一个或多个列的数据值[IRowsetChange:SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx)。|  
|[撤消](../../data/oledb/crowset-undo.md)|撤消对某一行自上次读取后进行任何更改或[更新](../../data/oledb/crowset-update.md)。|  
|[更新](../../data/oledb/crowset-update.md)|传输任何挂起的上次提取或更新以来对当前行所做的更改。|  
|[UpdateAll](../../data/oledb/crowset-updateall.md)|传输任何挂起的上次提取或更新以来对所有行所做的更改。|  
  
## <a name="remarks"></a>备注  
 在 OLE DB 行集是通过该程序设置和检索数据的对象。  
  
 此类并不是可实例化传递，但作为模板参数传递给`CTable`或`CCommand`(`CRowset`是默认设置)。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [DBViewer 示例](../../visual-cpp-samples.md)   
 [MultiRead 的示例](../../visual-cpp-samples.md)   
 [MultiRead 的属性示例](../../visual-cpp-samples.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)