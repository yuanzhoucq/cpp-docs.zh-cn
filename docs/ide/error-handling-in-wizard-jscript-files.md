---
title: "向导 JScript 文件中的错误处理 | Microsoft Docs"
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
  - "错误处理, JScript"
  - "JScript, 处理错误"
  - "向导 JScript 错误处理"
ms.assetid: 6df3ba46-7ab6-484c-ac45-b08f4b6a5900
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 向导 JScript 文件中的错误处理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建向导时，项目包含 Default.js 和 Common.js 文件。  使用这些文件自定义项目。  有关更多信息，请参见 [JScript 文件](../ide/jscript-file.md)。  
  
 项目应包含错误处理。  下面的代码为您提供一个此类代码的示例。  
  
### 在 JScript 中处理错误  
  
1.  若要在用户单击“完成”时捕捉错误，请输入以下代码：  
  
    ```  
    function OnFinish(selProj, Class)  
    {  
       try  
       {  
          .....  
       }  
       catch(e)  
       {  
          if (e.description.length != 0)  
             SetErrorInfo(e.description, e.number);  
          return e.number  
       }  
    }  
    ```  
  
2.  从脚本中调用的任何 Helper 脚本函数引发 `e`：  
  
    ```  
    function ExtenderFromType(strVariableType)  
    {  
       try  
       {  
          ....  
       }  
       catch(e)  
       {  
          throw e;  
       }  
    }  
    ```  
  
3.  如果参数 **PREPROCESS\_FUNCTION** 在 [.vsz 文件](../ide/dot-vsz-file-project-control.md)中，向导调用 [CanAddATLClass](../ide/jscript-functions-for-cpp-wizards.md)。  失败时使用 [SetErrorInfo](../ide/seterrorinfo.md) 并返回 **false**：  
  
    ```  
    function CanAddATLClass(oProj, oObject)  
    {  
       try  
       {  
          if (!IsATLProject(oProj))  
          {  
             if (!IsMFCProject(oProj, true))  
             {     
                var L_CanAddATLClass_Text = "ATL classes can only be added  
     to ATL, MFC EXE and MFC regular DLL projects.";  
                wizard.ReportError(L_CanAddATLClass_Text);  
                return false;  
             }  
             else  
             {  
                .....  
                var bRet = AddATLSupportToProject(oProj);  
                .....  
                return bRet;  
             }  
          }  
          return true;  
       }  
       catch(e)  
       {  
          throw e;  
       }  
    }  
    ```  
  
4.  如果必须返回到**新建项目**或**添加新项**对话框，则请返回到 **VS\_E\_WIZBACKBUTTONPRESS**：  
  
    ```  
    function OnFinish(selProj, Class)  
    {  
       ....  
       if (!CheckAddtoProject(selProj))  
       {  
          return VS_E_WIZARDBACKBUTTONPRESS;  
       }  
    }  
    ```  
  
## 请参阅  
 [为向导创建的文件](../ide/files-created-for-your-wizard.md)   
 [自定义向导](../ide/customizing-your-wizard.md)