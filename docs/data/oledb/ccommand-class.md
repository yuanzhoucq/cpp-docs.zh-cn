---
title: CCommand 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
dev_langs:
- C++
helpviewer_keywords:
- CCommand class
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 667e86c173a7001ae22036cb1f0dd8f3fbfcf6a2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096894"
---
# <a name="ccommand-class"></a>CCommand 类
提供设置和执行命令的方法。  
  
## <a name="syntax"></a>语法

```cpp
template <class TAccessor = CNoAccessor,  
          template <typename T> class TRowset = CRowset,  
          class TMultiple = CNoMultipleResults>  
class CCommand :   
           public CAccessorRowset <TAccessor, TRowset>,  
           public CCommandBase,  
           public TMultiple  
```  
  
#### <a name="parameters"></a>参数  
 `TAccessor`  
 您希望命令使用的访问器类的类型（如 `CDynamicParameterAccessor`、`CDynamicStringAccessor` 或 `CEnumeratorAccessor`）。 默认值为 `CNoAccessor`，它指定该类不支持参数或输出列。  
  
 `TRowset`  
 您希望命令使用的行集类的类型（如 `CArrayRowset` 或 `CNoRowset`）。 默认值为 `CRowset`。  
  
 `TMultiple`  
 若要使用的 OLE DB 命令时，可以返回多个结果，指定[CMultipleResults](../../data/oledb/cmultipleresults-class.md)。 否则，请使用[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)。 有关详细信息，请参阅[IMultipleResults](https://msdn.microsoft.com/en-us/library/ms721289.aspx)。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[关闭](../../data/oledb/ccommand-close.md)|关闭当前命令。|  
|[GetNextResult](../../data/oledb/ccommand-getnextresult.md)|在使用多个结果集时提取下一个结果。|  
|[打开](../../data/oledb/ccommand-open.md)|执行并选择性地绑定命令。|  
  
### <a name="inherited-methods"></a>继承的方法  
  
|||  
|-|-|  
|[创建](../../data/oledb/ccommand-create.md)|为指定会话创建新命令，然后设置命令文本。|  
|[CreateCommand](../../data/oledb/ccommand-createcommand.md)|创建新的命令。|  
|[GetParameterInfo](../../data/oledb/ccommand-getparameterinfo.md)|获取命令的参数、参数名称和参数类型的列表。|  
|[准备](../../data/oledb/ccommand-prepare.md)|验证并优化当前命令。|  
|[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)|在必要时释放参数访问器，然后释放命令。|  
|[SetParameterInfo](../../data/oledb/ccommand-setparameterinfo.md)|指定每个命令参数的本机类型。|  
|[Unprepare](../../data/oledb/ccommand-unprepare.md)|放弃当前命令执行计划。|  
  
## <a name="remarks"></a>备注  
 当您需要执行基于参数的操作或执行命令时，请使用此类。 如果你只需要打开简单行集合，请使用[CTable](../../data/oledb/ctable-class.md)相反。  
  
 使用的访问器类可确定绑定参数和数据的方法。  
  
 请注意，不能将存储过程与 Jet 的 OLE DB 提供程序一起使用，因为该提供程序不支持存储过程（查询字符串中只允许使用常数）。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)