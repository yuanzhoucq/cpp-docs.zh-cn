---
title: "CDaoErrorInfo 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoErrorInfo 结构"
  - "DAO（数据访问对象）, 错误集合"
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CDaoErrorInfo 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoErrorInfo` 结构包含有关用于数据访问对象定义错误对象的信息 \(DAO\)。  
  
## 语法  
  
```  
  
      struct CDaoErrorInfo  
{  
   long m_lErrorCode;  
   CString m_strSource;  
   CString m_strDescription;  
   CString m_strHelpFile;  
   long m_lHelpContext;  
};  
```  
  
#### 参数  
 *m\_lErrorCode*  
 数值 DAO 错误代码。  参见主题“Trappable 数据访问错误”DAO 帮助。  
  
 *m\_strSource*  
 最初产生错误的对象或应用程序的名称。  表示源属性指定最初产生错误的对象的字符串表达式；通常表达式是对象的类名。  有关详细信息，请参见主题“源属性”DAO 帮助。  
  
 *m\_strDescription*  
 描述性字符串与错误。  有关详细信息，请参见主题“Description 属性”DAO 帮助。  
  
 *m\_strHelpFile*  
 Microsoft Windows 帮助文件的完全限定路径。  有关详细信息，请参见主题“，HelpContext Helpfile 属性”DAO 帮助。  
  
 *m\_lHelpContext*  
 一个主题的上下文 ID。Microsoft Windows 帮助文件。  有关详细信息，请参见主题“，HelpContext Helpfile 属性”DAO 帮助。  
  
## 备注  
 MFC DAO 不封装类中的错误对象。  相反，类提供访问 [CDaoException](../../mfc/reference/cdaoexception-class.md) 中 DAO **DBEngine** 对象包含的错误集合的接口，还包含所有工作区的对象。  在 MFC DAO 操作引发可以捕获的 `CDaoException` 对象，则 MFC 填充 `CDaoErrorInfo` 结构并将其存储在对象的异常 [m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md) 成员。\(如果选择直接调用 DAO，必须调用异常对象的函数 [GetErrorInfo](../Topic/CDaoException::GetErrorInfo.md) 成员填充 `m_pErrorInfo`。\)  
  
 DAO 有关处理错误的更多信息，请参见知识库文章 [异常：数据库异常](../../mfc/exceptions-database-exceptions.md)。  有关相关信息，请参见主题“错误对象”DAO 帮助。  
  
 [CDaoException::GetErrorInfo](../Topic/CDaoException::GetErrorInfo.md) 成员函数检索的信息在 `CDaoErrorInfo` 结构存储。  检查来自在异常处理程序捕获的 `CDaoException` 对象的 [m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md) 数据成员，或者从您显式创建以便检查错误可能发生在一直接调用 DAO 过程到的 `CDaoException` 对象调用 `GetErrorInfo` 的连接。  `CDaoErrorInfo` 还定义了函数调试版本的 `Dump` 成员。  可以使用 `Dump` 转储 `CDaoErrorInfo` 对象的内容。  
  
## 要求  
 **页眉：** afxdao.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoException Class](../../mfc/reference/cdaoexception-class.md)