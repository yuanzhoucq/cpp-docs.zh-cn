---
title: "Registry Scripting Examples | Microsoft Docs"
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
  - "registrar scripts [ATL]"
  - "注册表, Registrar"
  - "脚本编写, 示例"
  - "脚本, Registrar scripts"
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Registry Scripting Examples
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题中的脚本的示例演示如何将该密钥添加到系统注册表中，控制器注册COM服务器，并指定多个分析树。  
  
## 添加一个项。HKEY\_CURRENT\_USER  
 以下分析树声明将唯一键到系统注册表的简单脚本。  具体而言，该脚本添加键，`MyVeryOwnKey`，若要 `HKEY_CURRENT_USER`。  它也进行 `HowGoesIt?` 的默认字符串值转换为新的项:  
  
```  
HKEY_CURRENT_USER  
{  
   'MyVeryOwnKey' = s 'HowGoesIt?'  
}  
```  
  
 此脚本可以轻松地扩展定义多个子如下所示:  
  
```  
HKCU  
{  
   'MyVeryOwnKey' = s 'HowGoesIt?'  
   {  
      'HasASubkey'  
      {  
         'PrettyCool?' = d '55'  
         val 'ANameValue' = s 'WithANamedValue'  
      }  
   }  
}  
```  
  
 现在，该脚本添加一个子级，`HasASubkey`，若要 `MyVeryOwnKey`。  此子级，它将 `PrettyCool?` 子项\(使用默认 `DWORD` 值为55\)和一个名为的 `ANameValue` 值\(与 `WithANamedValue`的字符串值）。  
  
##  <a name="_atl_register_the_registrar_com_server"></a> 控制器注册COM服务器  
 下面的脚本注册控制器COM服务器。  
  
```  
HKCR  
{  
   ATL.Registrar = s 'ATL Registrar Class'  
   {  
      CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'  
   }  
   NoRemove CLSID  
   {  
      ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} =  
                   s 'ATL Registrar Class'  
      {  
         ProgID = s 'ATL.Registrar'  
         InprocServer32 = s '%MODULE%'  
         {  
            val ThreadingModel = s 'Apartment'  
         }  
      }  
   }  
}  
```  
  
 在运行时，此分析树添加 `ATL.Registrar` 键。`HKEY_CLASSES_ROOT`。  此新项，然后:  
  
-   指定 `ATL Registrar Class`，键的默认值字符串值。  
  
-   添加 `CLSID` 作为子级。  
  
-   为 `CLSID`指定 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。  （此值是控制器的CLSID用于 `CoCreateInstance`的使用。）  
  
 因为 `CLSID` 共享，在注销模式下不应将其移除。  语句，`NoRemove CLSID`，通过指示执行此在注册模式将打开并忽略 `CLSID` 在注销模式。  
  
 `ForceRemove` 语句通过移除项和所有提供一种管理功能其子级在重新创建密钥之前。  如果子项的名称已更改，这会很有用。  此脚本的示例中，`ForceRemove` 检查 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` 是否已存在。  如果它，`ForceRemove`:  
  
-   递归删除 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` 及其所有子级。  
  
-   重新创建 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。  
  
-   添加 `ATL Registrar Class`，`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`的默认字符串值。  
  
 分析树现在添加两个新的子级。`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。  第一个关键，`ProgID`，获取是ProgID的默认字符串值。  第二个关键，`InprocServer32`，获取默认字符串值，`%MODULE%`，是节解释的预处理器值，[使用可替换参数\(控制器的预处理器\)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)，本文。  `InprocServer32` 还获取命名值，`ThreadingModel`，与 `Apartment`的字符串值。  
  
## 指定多个分析树  
 若要指定多个脚本中的分析树，将一个树在另一个末尾。  例如，下面的脚本添加键，`MyVeryOwnKey`，若要 `HKEY_CLASSES_ROOT` 和 `HKEY_CURRENT_USER`的分析树:  
  
```  
HKCR  
{  
   'MyVeryOwnKey' = s 'HowGoesIt?'  
}  
HKEY_CURRENT_USER  
{  
   'MyVeryOwnKey' = s 'HowGoesIt?'  
}  
```  
  
> [!NOTE]
>  在注册器脚本，4K是最大标记范围。  （标记是语法中的所有可识别的元素。）在前面的脚本的示例中，`HKCR`、 `HKEY_CURRENT_USER`、 `'MyVeryOwnKey'`和 `'HowGoesIt?'` 是所有标记。  
  
## 请参阅  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)