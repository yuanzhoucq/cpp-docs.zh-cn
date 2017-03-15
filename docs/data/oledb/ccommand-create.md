---
title: "CCommand::Create | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CCommand.Create"
  - "CCommand::Create"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Create 方法 [C++]"
ms.assetid: e4bede7a-68bd-491a-97f4-89b03d45cd24
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CCommand::Create
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用 [CCommand::CreateCommand](../../data/oledb/ccommand-createcommand.md) 创建指定的会话的命令，然后调用 [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) 指定命令文本。  
  
## 语法  
  
```  
  
      HRESULT CCommandBase::Create(  
   const CSession& session,   
   LPCWSTR wszCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT  
) throw ( );  
HRESULT CCommandBase::Create(  
   const CSession& session,   
   LPCSTR szCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT  
) throw ( );  
```  
  
#### 参数  
 `session`  
 \[in\] 的会话创建的命令。  
  
 `wszCommand`  
 \[in\] 为命令字符串的 Unicode 文本的指针。  
  
 `szCommand`  
 \[in\] 为命令字符串 \(ANSI 文本的指针。  
  
 `guidCommand`  
 \[in\] 将分析指定语法和一般规则使提供程序可以使用文本命令的 GUID。  有关方言的说明，请参阅《*OLE DB 程序员参考》\) 中的*[ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx)。  
  
## 返回值  
 标准 `HRESULT`。  
  
## 备注  
 **创建** 采用 Unicode 第一个命令字符串。  **创建** 第二个窗体接受 ANSI 命令字符串 \(提供的用于向后兼容现有 ANSI 应用程序\)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)