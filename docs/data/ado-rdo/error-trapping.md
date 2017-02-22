---
title: "错误捕获 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], 错误捕获"
  - "错误捕获 [C++]"
ms.assetid: c509b089-a542-44be-8f22-dc5832967a48
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 错误捕获
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在数据绑定中，错误捕获来自两个源：错误事件和错误对象。  
  
##  <a name="vcreferrortrappingviaerrorevents"></a> 通过错误事件捕获错误  
 ADO 数据控件和 RDO RemoteData 控件数据控件都具有错误事件。  通常，设置错误事件处理程序。  事件处理程序具有以下签名。  
  
```  
void CMyDlg::OnErrorAdodc1(long ErrorNumber,  
                           BSTR* FAR Description,  
                           long Scode,  
                           LPCTSTR Source,  
                           LPCTSTR HelpFile,  
                           long HelpContext,  
                           BOOL FAR* fCancelDisplay)  
```  
  
 Description 字段一般情况下都被填充，而 ErrorNumber 和 Scode 字段只在 COM 错误事件中被填充。  标准的事件处理程序在消息框中显示 Description 字段。  例如：  
  
```  
{  
   USES_CONVERSION;     
// note: have to include the ATL file ATLConv.h to use the ATL conversion macros  
   ::AfxMessageBox(OLE2T(*Description), MB_OK);  
}  
```  
  
 然而，ADO 数据控件和 RDO RemoteData 控件已被设置为捕获错误事件，因此不需要编码。  
  
##  <a name="vcreferrortrappingviaerrorobjects"></a> 通过错误对象捕获错误  
 ADO 和 RDO 都具有错误对象。  当生成[包装类](../../data/ado-rdo/wrapper-classes.md)时，RDO RemoteData 控件生成错误对象的包装，而 ADO 数据控件不生成。  
  
 ADO 数据控件自动显示 ADO 错误信息。  
  
## 请参阅  
 [在 Visual C\+\+ 中使用 ActiveX 控件进行数据绑定](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)