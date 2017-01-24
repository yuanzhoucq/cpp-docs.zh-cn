---
title: "Understanding Parse Trees | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "parse trees"
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Understanding Parse Trees
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以定义一个或多个在您的管理员脚本的分析树，每个分析树具有以下形式:  
  
```  
<root key>{<registry expression>}+  
```  
  
 其中：  
  
```  
<root key> ::=  HKEY_CLASSES_ROOT | HKEY_CURRENT_USER |  
               HKEY_LOCAL_MACHINE | HKEY_USERS |  
               HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA |  
               HKEY_CURRENT_CONFIG | HKCR | HKCU |  
               HKLM | HKU | HKPD | HKDD | HKCC  
<registry expression> ::= <Add Key> | <Delete Key>  
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>  
              [<Key Value>][{< Add Key>}]  
<Delete Key> ::=  Delete<Key Name>  
<Key Name> ::= '<AlphaNumeric>+'  
<AlphaNumeric> ::= any character not NULL, i.e. ASCII 0  
<Key Value> ::== <Key Type><Key Name>  
<Key Type> ::= s | d  
<Key Value> ::= '<AlphaNumeric>'  
```  
  
> [!NOTE]
>  `HKEY_CLASSES_ROOT` 和 `HKCR` 等效，`HKEY_CURRENT_USER` 和 `HKCU` 等效，等等。  
  
 分析树可以添加多个键和子级。\<root key\>。  在这种情况下，将保持子级的处理打开，直到该分析器完成分析其所有子级。  此方法比每次运行有效在唯一键，如下面的示例所示:  
  
```  
HKEY_CLASSES_ROOT  
{  
   'MyVeryOwnKey'  
   {  
      'HasASubKey'  
      {  
         'PrettyCool?'  
      }  
   }  
}  
```  
  
 此处，管理员首次打开\(创建\) `HKEY_CLASSES_ROOT\MyVeryOwnKey`。  然后参见 `MyVeryOwnKey` 有一个子级。  而不是关闭键 `MyVeryOwnKey`，管理员保留句柄并打开\(创建\)使用此父处理，`HasASubKey`。  （系统注册表可以更慢，在父句柄不是打开的。）因此，打开 `HKEY_CLASSES_ROOT\MyVeryOwnKey` 然后打开的 `HasASubKey` 和 `MyVeryOwnKey` 作为父比打开的 `MyVeryOwnKey`、结束 `MyVeryOwnKey`然后打开的 `MyVeryOwnKey\HasASubKey`express。  
  
## 请参阅  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)