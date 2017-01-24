---
title: "GetCodeForDllRegisterServer | Microsoft Docs"
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
  - "GetCodeForDllRegisterServer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForDllRegisterServer 方法"
ms.assetid: 2fe733ad-3f1e-4020-9ce3-68956da7d41d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetCodeForDllRegisterServer
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取用于注册服务器的适当代码。  
  
## <a name="syntax"></a>语法  
  
```  
  
      function GetCodeForDllRegisterServer(   
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
 一个包含用于注册服务器的代码的字符串  
  
## <a name="remarks"></a>备注  
 调用该成员函数以检索用于注册服务器的适当代码︰  
  
|行号|代码|  
|-----------------|----------|  
|0|AFX_MANAGE_STATE(AfxGetStaticModuleState());|  
|1|_AtlModule.UpdateRegistryAppId(TRUE);|  
|2|HRESULT hRes = _AtlModule.RegisterServer(TRUE);|  
|3|如果 (hRes ！ =，则为 S_OK)|  
|4|\treturn hRes;|  
|5|if （！。COleObjectFactory::UpdateRegistryAll(TRUE))|  
|6|\treturn ResultFromScode(SELFREG_E_CLASS);|  
|7|返回，则为 S_OK;|  
  
 为每个返回的行 `GetCodeForDllRegisterServer` 添加一个前导制表符 (`\t`) 和一个尾随"CR-LF"（回车-换行） 字符对 (`\r\n`)。  
  
## <a name="example"></a>示例  
  
```  
// Get the lines numbered 2 and 3 above  
GetCodeForDllRegisterServer(2, 3)  
  
// returns the following string  
// "\tHRESULT hRes = _AtlModule.RegisterServer(TRUE);\r\n\tif (hRes != S_OK)\r\n"  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [用公共 JScript 函数自定义 c + + 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 c + + 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [GetCodeForDllUnregisterServer](../ide/getcodefordllunregisterserver.md)