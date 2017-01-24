---
title: "GetCodeForDllCanUnloadNow | Microsoft Docs"
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
  - "GetCodeForDllCanUnloadNow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForDllCanUnloadNow 方法"
ms.assetid: 24ee3ef7-45be-4778-99e8-6df493f0782b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetCodeForDllCanUnloadNow
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取用于卸载 DLL 的适当代码。  
  
## <a name="syntax"></a>语法  
  
```  
  
      function GetCodeForDllCanUnloadNow(   
   nLineStart,   
   nLineEnd    
);  
```  
  
#### <a name="parameters"></a>参数  
 `nLineStart`  
 函数的开始处的从零开始的行号。  
  
 `nLineEnd`  
 在函数末尾从零开始的行数。  
  
## <a name="return-value"></a>返回值  
 包含用于卸载 DLL 代码的字符串。  
  
## <a name="remarks"></a>备注  
 调用该成员函数以检索用于卸载 DLL 的适当代码。 调用此函数通过串联您指定的数组元素创建一个字符串。  
  
 下表显示用于卸载 DLL 的代码。  
  
|行号|代码|  
|-----------------|----------|  
|0|AFX_MANAGE_STATE(AfxGetStaticModuleState());|  
|1|如果 (_AtlModule.GetLockCount() > 0)|  
|2|\treturn S_FALSE;|  
|3|返回，则为 S_OK;|  
  
 为每个返回的行 `GetCodeForDllCanUnloadNow` 添加一个前导制表符 (`\t`) 和一个尾随"CR-LF"（回车-换行） 字符对 (`\r\n`)。  
  
## <a name="example"></a>示例  
  
```  
// Get the lines numbered 1 and 2 above  
GetCodeForDllCanUnloadNow(1, 2)  
  
// returns the following string  
// "\tif (_AtlModule.GetLockCount() > 0)\r\n\t\treturn S_FALSE;\r\n"  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [用公共 JScript 函数自定义 c + + 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 c + + 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [GetCodeForDllGetClassObject](../ide/getcodefordllgetclassobject.md)   
 [GetCodeForExitInstance](../ide/getcodeforexitinstance.md)