---
title: "Ccommand:: Open |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 4c9b8f31-faf3-452d-9a29-3d3e5f54d6f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bf4d30382224cd1fe85d12623acdcb90b0dee1bd
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ccommandopen"></a>CCommand::Open
执行并选择性地绑定命令。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCWSTR wszCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  


HRESULT Open(const CSession& session,  
   LPCSTR szCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  


HRESULT Open(const CSession& session,  
   INT szCommand = NULL,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  


HRESULT Open(DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `session`  
 [in]在其中执行命令会话。  
  
 `wszCommand`  
 [in]若要执行，该命令传递为 Unicode 字符串。 可以是**NULL**时使用`CAccessor`，在这种情况下，将从传递给的值检索命令[DEFINE_COMMAND](../../data/oledb/define-command.md)宏。 请参阅[ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx)中*OLE DB 程序员参考*有关详细信息。  
  
 `szCommand`  
 [in]与相同`wszCommand`，但此参数将 ANSI 命令字符串。 此方法的第四个形式可以采用 NULL 值。 有关详细信息的本主题中后面，请参阅"备注"。  
  
 *pPropSet*  
 [in]指向数组的指针[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)包含属性和要设置值的结构。 请参阅[属性设置和属性组](https://msdn.microsoft.com/en-us/library/ms713696.aspx)中*OLE DB 程序员参考*Windows SDK 中。  
  
 `pRowsAffected`  
 [输入/输出]指向内存其中返回某一命令受影响的行数的指针。 如果 *\*pRowsAffected*是**NULL**，会返回任何行。 否则为**打开**设置 *`pRowsAffected`根据以下条件：  
  
|如果|Then|  
|--------|----------|  
|**CParamSets**元素`pParams`大于 1|*`pRowsAffected` 表示由指定的执行过程中的参数集的所有受影响的行总数。|  
|受影响的行数不可用|*`pRowsAffected` 设置为-1。|  
|该命令不会更新、 删除或插入行|*`pRowsAffected` 未定义。|  
  
 `guidCommand`  
 [in]分析命令文本中指定的语法和一般规则要使用的提供程序的 GUID。 请参阅[ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx)和[ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709757.aspx)中*OLE DB 程序员参考*有关详细信息。  
  
 `bBind`  
 [in]指定是否在正在执行后自动绑定命令。 默认值是**true**，这将导致产生命令自动绑定。 设置`bBind`到**false**阻止自动绑定命令，以便你可以手动绑定。 （手动绑定是 OLAP 用户的特别感兴趣。）  
  
 `ulPropSets`  
 [in]数[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)结构*pPropSet*自变量。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 前三个窗体**打开**需要会话，创建一个命令，并执行该命令，根据需要绑定任何参数。  
  
 第一种形式的**打开**将 Unicode 命令字符串，并且没有默认值。  
  
 第二种形式的**打开**采用 ANSI 命令字符串和 （为了向后兼容现有的 ANSI 应用程序提供） 没有默认值。  
  
 第三种形式**打开**允许命令的字符串为 NULL，由于类型而`int`默认值为 NULL。 它旨在供调用`Open(session, NULL);`或`Open(session);`因为 NULL 的类型`int`。 此版本要求和断言`int`参数为 NULL。  
  
 使用的第四个形式**打开**当你已创建了一个命令并且想要执行单个[准备](../../data/oledb/ccommand-prepare.md)和多个执行。  
  
> [!NOTE]
>  **打开**调用**执行**，从而又会调用`GetNextResult`。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)