---
title: "CanUseFileName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CanUseFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanUseFileName 方法"
ms.assetid: 60b669fa-9484-4435-b502-78ec8e960a00
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CanUseFileName
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检查文件是否存在。  如果文件存在并且不受限制，则向导提示用户将要添加的代码合并到现有文件。  
  
## 语法  
  
```  
  
      function CanUseFileName(   
   strFileName,   
   bCheckIfMidlHeader,   
   bCannotExist,   
   bSetMergeFlag    
);  
```  
  
#### 参数  
 `strFileName`  
 要检查的文件名。  
  
 *bCheckIfMidlHeader*  
 设置为 **true** 以检查文件名是否由 MIDL 生成。  
  
 *bCannotExist*  
 设置为 **true** 以检查文件名是否已经存在并且无法覆盖。  
  
 *bSetMergeFlag*  
 设置为 **true** 以包含 MERG\_FILE 符号，它指示用户可以将代码合并到现有文件名。  
  
## 返回值  
 如果 `strFileName` 唯一，或者如果代码可追加到现有文件，则为 **true**；否则为 **false**。  
  
## 备注  
 调用该函数以检查文件名是否存在。  如果文件名存在，并且不是由 MIDL 创建的，或者另外不受限制，则函数提示用户将新代码合并到现有文件。  
  
 如果文件名不存在并且不受限制，则创建指定名称的文件。  
  
 如果文件名已由 MIDL 创建，或者另外受限制，则向导显示错误信息。  
  
## 示例  
  
```  
case "HTML_FILE":  
if (!HTML_FILE.disabled)  
   {  
   if (!window.external.FindSymbol("HTML_FILE_VALID"))  
      {  
      bValid = CanUseFileName(obj.value, false, true);  
      if (!bValid)  
      break;  
      window.external.AddSymbol("HTML_FILE_VALID", true)  
      }  
   }  
   bValid = window.external.ValidateFile(HTML_FILE.value, vsCMValidateFileExtHtml);  
   break;   
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)