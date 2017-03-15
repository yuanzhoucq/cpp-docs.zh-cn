---
title: "GetRuntimeErrorDesc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetRuntimeErrorDesc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ConversionError 方法"
  - "GetRuntimeErrorDesc 方法"
  - "RangeError 方法"
  - "ReferenceError 方法"
  - "RegExpError 方法"
  - "SyntaxError 方法"
  - "TypeError 方法"
  - "URIError 方法"
ms.assetid: d56fdd2e-6ad0-4c49-9e98-bcf0105e1b12
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# GetRuntimeErrorDesc
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

返回异常类型的说明。  
  
## 语法  
  
```  
  
      function GetRuntimeErrorDesc(   
   strRuntimeErrorName    
);  
```  
  
#### 参数  
 *strRuntimeErrorName*  
 已发生的异常类型的名称。  
  
## 返回值  
 异常类型的说明。  
  
## 备注  
 返回异常类型的说明。  可以是以下异常类型之一：  
  
|异常类型|说明|  
|----------|--------|  
|ConversionError|每当尝试将一个对象转换为它无法转换的内容时发生。|  
|RangeError|当为函数提供的参数超过了它允许的范围时发生。  例如，当尝试构造的 `Array` 对象的长度不是有效的正整数时，发生此错误。|  
|ReferenceError|当检测到无效引用时发生。  例如，如果所需的引用为 null，将发生此错误。|  
|RegExpError|当正则表达式出现编译错误时发生。  正则表达式被编译后就不会发生此错误。  例如，如果声明正则表达式的模式使用了无效的语法或使用了 *i*、*g* 或 *m* 以外的标志，或者多次包含同一个标志，将发生此错误。|  
|SyntaxError|当对源文本进行语法分析并且源文本不合乎正确语法时发生。  例如，当调用 `eval` 函数的参数不是有效的程序文本时，将发生此错误。|  
|TypeError|每当操作数的实际类型与所需类型不匹配时发生。  例如，如果在不是对象的内容上进行函数调用或者该内容不支持该调用时，发生此错误。|  
|URIError|当检测到非法的统一资源标识符 \(URI\) 时发生。  例如，在正编码或解码的字符串中发现非法字符时，发生此错误。|  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)