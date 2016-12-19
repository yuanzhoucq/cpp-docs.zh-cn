---
title: "Invoking Scripts | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StringRegister"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "脚本, invoking registry in ATL"
  - "StringRegister method"
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Invoking Scripts
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[使用可替换参数\(控制器的预处理器\)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) 讨论替换映射和提到控制器方法 **AddReplacement**。  管理员还有其他八个方法特定于脚本，因此，所有在下表中所述。  
  
|方法|语法\/声明|  
|--------|------------|  
|**ResourceRegister**|**HRESULT ResourceRegister\( LPCOLESTR**  *resFileName* **, UINT**  `nID` **, LPCOLESTR**  `szType`\);<br /><br /> 注册模块中的资源包含的脚本。  *resFileName* 指示UNC路径添加到模块中。  `nID` 和 `szType` 包含资源的ID和类型，分别。|  
|**ResourceUnregister**|**HRESULT ResourceUnregister\( LPCOLESTR**  *resFileName* **, UINT**  `nID` **, LPCOLESTR**  `szType`\);<br /><br /> 取消模块中的资源包含的脚本。  *resFileName* 指示UNC路径添加到模块中。  `nID` 和 `szType` 包含资源的ID和类型，分别。|  
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz\( LPCOLESTR**  *resFileName* **, LPCOLESTR**  *szID* **, LPCOLESTR**  `szType`\);<br /><br /> 注册模块中的资源包含的脚本。  *resFileName* 指示UNC路径添加到模块中。  *szID* 和 `szType` 包含资源的字符串标识符和类型，它们。|  
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz\( LPCOLESTR**  *resFileName* **, LPCOLESTR**  *szID* **, LPCOLESTR**  `szType`\);<br /><br /> 取消模块中的资源包含的脚本。  *resFileName* 指示UNC路径添加到模块中。  *szID* 和 `szType` 包含资源的字符串标识符和类型，它们。|  
|**FileRegister**|**HRESULT FileRegister\( LPCOLESTR**  *文件名* \);<br /><br /> 注册文件中的脚本。  *文件名* 是UNC路径包含的文件\(或\)是一个资源脚本。|  
|**FileUnregister**|**HRESULT FileUnregister\( LPCOLESTR**  *文件名* \);<br /><br /> 注销文件中的脚本。  *文件名* 是UNC路径包含的文件\(或\)是一个资源脚本。|  
|**StringRegister**|**HRESULT StringRegister\( LPCOLESTR**  *数据* \);<br /><br /> 注册字符串中的脚本。  *数据* 包含该脚本。|  
|**StringUnregister**|**HRESULT StringUnregister\( LPCOLESTR**  *数据* \);<br /><br /> 注销字符串中的脚本。  *数据* 包含该脚本。|  
  
 **ResourceRegisterSz** 和 **ResourceUnregisterSz**，类似于 **ResourceRegister** 和 **ResourceUnregister**，但是，允许您指定字符串标识符。  
  
 方法 **FileRegister** 和 **FileUnregister** 很有用，如果不需要在资源的脚本，或者您希望在其自己的文件的脚本。  方法 **StringRegister** 和 **StringUnregister** 在动态分配的字符串允许.rgs文件中。  
  
## 请参阅  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)