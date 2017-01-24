---
title: "向导 HTML 文件中的错误处理 | Microsoft Docs"
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
  - "错误处理, 文件错误检查"
  - "HTML, 错误处理"
ms.assetid: eb428a64-b681-4420-987d-92098bf98455
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 向导 HTML 文件中的错误处理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当创建具有用户界面的向导时，项目包含 .htm 文件。  使用这些文件自定义项目。  有关更多信息，请参见 [HTML 文件](../ide/html-files.md)。  
  
 项目应包含错误处理。  下面的代码为您提供一个此类代码的示例。  
  
### 在 HTML 中处理错误  
  
1.  当验证字段时，如果调用 DLL 中的验证方法（DLL 中应设置错误信息），请不带参数调用 `ReportError`。  
  
    ```  
    function ValidateInput()  
    {  
       if (!window.external.ValidateFile(HEADER_FILE.value))  
       {  
          ReportError();  
          HEADER_FILE.focus();  
          return false;  
       }  
    }  
    ```  
  
2.  当验证字段时，如果仅使用 HTML 脚本验证字段，请首先调用 `SetErrorInfo`，然后不带参数调用 `ReportError`。  
  
    ```  
    function OnWhatever()  
    {  
       if (!ValidateInput())  
          window.external.ReportErrror();  
       ....  
    }  
  
    function ValidateInput()  
    {  
       .....  
  
       if (HEADER_FILE.value == IMPL_FILE.value)  
       {  
          var L_ErrMsg_Text = "Header and implementation files cannot have the same name.";  
          SetErrorInfo(L_ErrMsg_Text);  
          bValid = false;  
       }  
       if (TYPE.value == "")  
       {  
          var L_ErrMsg4_Text = "Type cannot be blank.";  
          SetErrorInfo(L_ErrMsg4_Text);  
          bValid = false;  
       }  
       return bValid;  
    }  
    ```  
  
3.  带参数调用 `ReportError`：  
  
    ```  
    function ValidateInput()  
    {  
       if (!IsListed(strType))  
       {  
          var L_Invalid2_Text = "The variable type should be one of the types listed.";  
          window.external.ReportError(L_Invalid2_Text);  
          VariableType.focus();  
          return false;  
       }  
    }  
    ```  
  
4.  如果必须返回到**新建项目**或**添加新项**对话框，则请返回到 **VS\_E\_WIZBACKBUTTONPRESS**：  
  
    ```  
    try  
    {  
       oCM   = window.external.ProjectObject.CodeModel;  
    }  
    catch(e)  
    {  
       var L_NCBError_Text = "Cannot access the Class View information   
    file. Class View information will not be available.";  
       window.external.ReportError(L_NCBError_Text);  
       return VS_E_WIZARDBACKBUTTONPRESS;  
    ```  
  
## 请参阅  
 [为向导创建的文件](../ide/files-created-for-your-wizard.md)   
 [自定义向导](../ide/customizing-your-wizard.md)