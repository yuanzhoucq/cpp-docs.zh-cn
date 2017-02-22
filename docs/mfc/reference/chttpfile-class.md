---
title: "CHttpFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CHttpFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHttpFile class"
  - "HTTP 文件"
  - "HTTP requests, requesting and reading files"
ms.assetid: 399e7c68-bbce-4374-8c55-206e9c7baac6
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CHttpFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在HTTP服务器提供功能请求和读取文件。  
  
## 语法  
  
```  
class CHttpFile : public CInternetFile  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CHttpFile::CHttpFile](../Topic/CHttpFile::CHttpFile.md)|创建一个 `CHttpFile` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CHttpFile::AddRequestHeaders](../Topic/CHttpFile::AddRequestHeaders.md)|添加标头到请求发送到HTTP服务器。|  
|[CHttpFile::EndRequest](../Topic/CHttpFile::EndRequest.md)|关闭请求发送到具有 [SendRequestEx](../Topic/CHttpFile::SendRequestEx.md) 成员函数的一个HTTP服务器。|  
|[CHttpFile::GetFileURL](../Topic/CHttpFile::GetFileURL.md)|获取指定文件的URL。|  
|[CHttpFile::GetObject](../Topic/CHttpFile::GetObject.md)|获取目标直接宾语在请求于HTTP服务器。|  
|[CHttpFile::GetVerb](../Topic/CHttpFile::GetVerb.md)|获取用于对HTTP服务器的请求的谓词。|  
|[CHttpFile::QueryInfo](../Topic/CHttpFile::QueryInfo.md)|返回响应或请求标头从HTTP服务器。|  
|[CHttpFile::QueryInfoStatusCode](../Topic/CHttpFile::QueryInfoStatusCode.md)|检索该状态代码与HTTP请求并将其放在提供的 `dwStatusCode` 参数。|  
|[CHttpFile::SendRequest](../Topic/CHttpFile::SendRequest.md)|发送一个请求到HTTP服务器。|  
|[CHttpFile::SendRequestEx](../Topic/CHttpFile::SendRequestEx.md)|使用 `CInternetFile`，[写入](../Topic/CInternetFile::Write.md) 或 [WriteString](../Topic/CInternetFile::WriteString.md) 方法发送一个请求到HTTP服务器。|  
  
## 备注  
 如果您的Internet会话读取HTTP服务器的数据，必须创建 `CHttpFile`实例。  
  
 若要了解更多信息 `CHttpFile` 与其他MFC Internet选件类，请参见文章 [编程时WinInet的Internet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C文件](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CHttpFile`  
  
## 要求  
 **Header:** afxinet.h  
  
## 请参阅  
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CHttpConnection Class](../../mfc/reference/chttpconnection-class.md)