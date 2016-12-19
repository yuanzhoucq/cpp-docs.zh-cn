---
title: "CCommand::Open | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CCommand.Open"
  - "ATL::CCommand::Open"
  - "CCommand.Open"
  - "CCommand::Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open 方法"
ms.assetid: 4c9b8f31-faf3-452d-9a29-3d3e5f54d6f8
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCommand::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

执行和可选的绑定命令。  
  
## 语法  
  
```  
  
      HRESULT Open(  
   const CSession& session,  
   LPCWSTR wszCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
HRESULT Open(  
   const CSession& session,  
   LPCSTR szCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
HRESULT Open(  
   const CSession& session,  
   INT szCommand = NULL,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
HRESULT Open(  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
```  
  
#### 参数  
 `session`  
 \[in\] 执行命令的会话。  
  
 `wszCommand`  
 \[in\] 执行的命令，作为 Unicode 字符串传递。  可为 **NULL** 在使用 `CAccessor` 时，在这种情况下，将从传递给宏 [DEFINE\_COMMAND](../../data/oledb/define-command.md) 的值检索命令。  参见 *OLE DB 程序员参考* 中的 [ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) 查看详细信息。  
  
 `szCommand`  
 \[in\] 和 `wszCommand` 一样，但此参数采用 ANSI 命令字符串。  此方法的第四种形式可以接受空值。  之后参见本主题的“备注”了解详细信息。  
  
 *pPropSet*  
 \[in\] 对数组的指针包含属性和值的结构将 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)。  见[属性集和属性组](https://msdn.microsoft.com/en-us/library/ms713696.aspx)在 *OLE DB程序员参考*在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `pRowsAffected`  
 \[in\/out\] 返回命令影响的行计数的内存的指针。  如果 *\*pRowsAffected* 为 **NULL**，则没有行计数返回。  否则，按照以下条件 **打开** 设置 \*`pRowsAffected` :  
  
|如果|那么…|  
|--------|---------|  
|`pParams` 的 **cParamSets** 元素大于 1|\*`pRowsAffected` 表示在执行中指定的所有参数集影响的总行数。|  
|受影响行中的数量不可用|将 \*`pRowsAffected` 设置为 –1。|  
|此命令不能更新，不能删除，也不能插入行|\*`pRowsAffected` 是不确定的。|  
  
 `guidCommand`  
 \[in\] GUID 指定用于提供程序分析命令文本的语法和一般规则 。  参见 [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) 和 [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709757.aspx) 在 *OLE DB 程序员参考* 中了解详细信息。  
  
 `bBind`  
 \[in\] 指定是否在执行后自动绑定命令。  默认是 **true**，导致命令自动绑定。  设置 `bBind` 为 **false** 以阻止命令的自动绑定，以便手动绑定。\(OLAP 用户对手动绑定特别感兴趣。\)  
  
 `ulPropSets`  
 \[in\] [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 结构数。*pPropSet* 参数传递的。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 **打开** 前三种形式接受会话，创建命令，然后执行命令，绑定所需要所有参数。  
  
 **打开** 第一个形式采用 Unicode 命令字符串并没有默认值。  
  
 **打开** 第二个形式采用 ANSI 命令字符串和不带默认值 \(用于与现有 ANSI 应用程序向后兼容\)。  
  
 **打开** 第三个形式允许命令字符串为 NULL，由于具有默认 NULL 值的 `int` 类型。  因为 NULL 为 `int` 类型，所以它提供对 `Open(session, NULL);` 或 `Open(session);` 的调用。  此版本要求和维护 `int` 参数为 NULL。  
  
 如果已经创建命令，而且您希望完成一次 [Prepare （准备）](../../data/oledb/ccommand-prepare.md) 并执行多次，请使用 **打开** 的第四种形式。  
  
> [!NOTE]
>  **打开** 调用 **执行**，从而调用 `GetNextResult`。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)