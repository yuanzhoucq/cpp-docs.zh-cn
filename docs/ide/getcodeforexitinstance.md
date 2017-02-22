---
title: "GetCodeForExitInstance | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetCodeForExitInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForExitInstance 方法"
ms.assetid: 41fe3d79-a1f4-4bb5-b3f5-7859e255b4e7
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetCodeForExitInstance
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取 [ExitInstance](../Topic/CWinApp::ExitInstance.md) 终止该向导的代码。  
  
## <a name="syntax"></a>语法  
  
```  
  
      function GetCodeForExitInstance(   
   nLineStart,   
   nLineEnd    
)   
```  
  
#### <a name="parameters"></a>参数  
 `nLineStart`  
 函数的开始处的从零开始的行号。  
  
 `nLineEnd`  
 在函数末尾的从零开始的行号。  
  
## <a name="return-value"></a>返回值  
 包含用于退出向导实例的代码的字符串。  
  
## <a name="remarks"></a>备注  
 调用此成员函数以检索用于退出该向导的实例的相应代码︰  
  
|行号|ExitInstance 代码|  
|-----------------|-----------------------|  
|0|_AtlModule.RevokeClassObjects();|  
|1|返回 CWinApp::ExitInstance();|  
  
 为每个返回的行 `GetCodeForExitInstance` 添加一个前导制表符 (`\t`) 和一个尾随"CR-LF"（回车-换行） 字符对 (`\r\n`)。  
  
## <a name="example"></a>示例  
  
```  
if (!oExitInstance)  
   {  
      oExitInstance = oCWinApp.AddFunction("ExitInstance",   
      vsCMFunctionFunction, "BOOL", vsCMAddPositionEnd, vsCMAccessPublic,   
      strProjectCPP);  
      oExitInstance.BodyText = GetCodeForExitInstance(0, 1);  
   }  
// returns the following string  
// "\t_AtlModule.RevokeClassObjects();\r\n  
// \treturn CWinApp::ExitInstance();\r\n"  
else  
   {  
   oExitInstance.StartPointOf(vsCMPartBody,   
   vsCMWhereDefinition).CreateEditPoint().Insert(GetCodeForExitInstance(0,   
   0));  
// returns the following string  
// "\t_AtlModule.RevokeClassObjects();\r\n  
      oCM.Synchronize();  
   }  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [用公共 JScript 函数自定义 c + + 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 c + + 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [GetCodeForDllCanUnloadNow](../ide/getcodefordllcanunloadnow.md)   
 [GetCodeForInitInstance](../ide/getcodeforinitinstance.md)