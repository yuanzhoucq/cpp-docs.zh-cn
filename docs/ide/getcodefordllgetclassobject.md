---
title: "GetCodeForDllGetClassObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetCodeForDllGetClassObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForDllGetClassObject 方法"
ms.assetid: 67b61b3b-9784-494f-ba01-17bffa9941ff
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetCodeForDllGetClassObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检索 DLL 类对象的代码。  
  
## <a name="syntax"></a>语法  
  
```  
  
      function GetCodeForDllGetClassObject(   
   nLineStart,   
   nLineEnd    
);  
```  
  
#### <a name="parameters"></a>参数  
 `nLineStart`  
 函数的开始处的从零开始的行号。  
  
 `nLineEnd`  
 在函数末尾的从零开始的行号。  
  
## <a name="return-value"></a>返回值  
 一个字符串，包含用于获取类对象的代码。  
  
## <a name="remarks"></a>备注  
 调用此成员函数以检索的类对象的代码。 调用此函数通过串联您指定的数组元素创建一个字符串。  
  
 下表显示用于获取代码类对象︰  
  
|行号|代码|  
|-----------------|----------|  
|0|AFX_MANAGE_STATE(AfxGetStaticModuleState());|  
|1|如果 (S_OK = = _AtlModule.GetClassObject （rclsid、 riid、 ppv）)|  
|2|\treturn，则为 S_OK;|  
|3|返回 AfxDllGetClassObject rclsid、 riid (ppv）;|  
  
 为每个返回的行 `GetCodeForDllGetClassObject` 添加一个前导制表符 (`\t`) 和一个尾随"CR-LF"（回车-换行） 字符对 (`\r\n`)。  
  
## <a name="example"></a>示例  
  
```  
// Get the lines numbered 1 and 2 above  
GetCodeForDllGetClassObject(1, 2)  
  
// returns the following string  
// "\tif (S_OK == _AtlModule.GetClassObject(rclsid, riid, ppv))\r\n\t\treturn S_OK;\r\n"  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [用公共 JScript 函数自定义 c + + 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 c + + 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)