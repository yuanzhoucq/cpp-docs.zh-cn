---
title: "用于 C++ 向导的 JScript 函数 | Microsoft Docs"
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
  - "向导 JScript 方法"
  - "向导 JScript 方法, 创建 C++ 向导"
ms.assetid: f3046c56-cf67-4aaa-919e-8c066bfb6760
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用于 C++ 向导的 JScript 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

|||  
|-|-|  
|[AddATLSupportToProject](../ide/addatlsupporttoproject.md)|向 MFC 项目添加 ATL 支持。|  
|[AddCoclassFromFile](../ide/addcoclassfromfile.md)|将包含 coclass 的模板文件呈现并插入到项目的 .idl 文件中。|  
|[AddCommonConfig](../ide/addcommonconfig.md)|向项目中添加默认配置。|  
|[AddFilesToProject](../ide/addfilestoproject.md)|根据文件 Templates.inf 中的列表将所有文件添加到项目。|  
|[AddInterfaceFromFile](../ide/addinterfacefromfile.md)|将包含接口的模板文件呈现并插入到项目的 IDL 文件中。|  
|[CanAddATLClass](../ide/canaddatlclass.md)|由向导调用以验证该项目是否与即将运行的代码向导兼容（换句话说，它是否可以接受 ATL 类）。<br /><br /> 当参数 PREPROCESS\_FUNCTION 在[项目控件的 .vsz 文件](../ide/dot-vsz-file-project-control.md)中时，向导调用此函数，并检查 [Visual C\+\+ Code Model](http://msdn.microsoft.com/zh-cn/dd6452c2-1054-44a1-b0eb-639a94a1216b)是否可用。  如果代码模型不可用，该函数将报告错误并且返回 **false**。|  
|[CanAddClass](../ide/canaddclass.md)|当参数 PREPROCESS\_FUNCTION 在项目控件的 .vsz 文件中时，向导调用此函数。<br /><br /> 它验证 Visual C\+\+ 代码模型对象是否可用。  如果代码模型不可用，该函数将报告错误并且返回 **false**。|  
|[CanAddMFCClass](../ide/canaddmfcclass.md)|由向导调用以验证该项目是否与即将运行的代码向导兼容（换句话说，它是否可以接受 MFC 类）。<br /><br /> 当参数 PREPROCESS\_FUNCTION 在项目控件的 .vsz 文件中时，向导调用此函数。它检查 Visual C\+\+ 代码模型对象是否可用。  如果代码模型不可用，该函数将报告错误并且返回 **false**。|  
|[CanAddNonAttributed](../ide/canaddnonattributed.md)|指示项目是否同时支持特性化和非特性化的 ATL 对象。|  
|[CanUseFileName](../ide/canusefilename.md)|检查文件是否存在。  如果存在，则向导提示用户将要添加的代码合并到现有文件中。|  
|[ConvertProjectToAttributed](../ide/convertprojecttoattributed.md)|将 ATL 项目转换为特性化。|  
|[CreateInfFile](../ide/createinffile.md)|创建 Templates.inf 文件。|  
|[CreateProject](../ide/createproject.md)|创建 C\+\+ 项目。|  
|[CreateSafeName](../ide/createsafename.md)|生成 C\+\+ 友好名称。|  
|[DeleteFile](../ide/deletefile.md)|删除指定的文件。|  
|[DoesIncludeExist](../ide/doesincludeexist.md)|指示文件中是否存在 `#include` 语句。|  
|[GetCodeForDllCanUnloadNow](../ide/getcodefordllcanunloadnow.md)|检索卸载 DLL 所需的代码。|  
|[GetCodeForDllGetClassObject](../ide/getcodefordllgetclassobject.md)|检索 DLL 类对象的代码。|  
|[GetCodeForDllRegisterServer](../ide/getcodefordllregisterserver.md)|检索注册服务器所使用的代码。|  
|[GetCodeForDllUnregisterServer](../ide/getcodefordllunregisterserver.md)|检索注销服务器所使用的代码。|  
|[GetCodeForExitInstance](../ide/getcodeforexitinstance.md)|获取 `ExitInstance` 文本的 Helper 函数。|  
|[GetCodeForInitInstance](../ide/getcodeforinitinstance.md)|获取 [InitInstance](../Topic/CWinApp::InitInstance.md) 文本的 Helper 函数。|  
|[GetExportPragmas](../ide/getexportpragmas.md)|检索导出函数的杂注。|  
|[GetInterfaceClasses](../ide/getinterfaceclasses.md)|返回与接口关联的 `VCCodeClass` 对象。|  
|[GetInterfaceType](../ide/getinterfacetype.md)|返回接口类型（如 custom、dual、dispinterface、oleautomation）。|  
|[GetMaxID](../ide/getmaxid.md)|从该接口及其所有基的成员返回最高的 `dispid`。|  
|[GetMemberfunction](../ide/getmemberfunction.md)|根据给定名称返回函数对象。|  
|[GetProjectFile](../ide/getprojectfile.md)|返回每种项目类型的文件（.rc、.idl 等）的文件名。|  
|[GetProjectPath](../ide/getprojectpath.md)|返回项目的目录路径。|  
|[GetRuntimeErrorDesc](../ide/getruntimeerrordesc.md)|返回异常类型的说明。|  
|[GetUniqueFileName](../ide/getuniquefilename.md)|返回唯一的文件名。|  
|[IncludeCodeElementDeclaration](../ide/includecodeelementdeclaration.md)|将 include 语句添加到 `strInFile`，包括实现 `strCodeElemName` 的头（如果在项目中发现这样的头）。|  
|[InsertIntoFunction](../ide/insertintofunction.md)|Helper 函数，在 `AddATLSupportToProject` 中被调用以将代码插入 `InitInstance` 中。|  
|[IsATLProject](../ide/isatlproject.md)|指示项目是否基于 ATL。|  
|[IsAttributedProject](../ide/isattributedproject.md)|指示项目是否已特性化。|  
|[IsMFCProject](../ide/ismfcproject.md)|检查项目是否基于 MFC。|  
|[LineBeginsWith](../ide/linebeginswith.md)|Helper 函数，在 `InsertIntoFunction` 中被调用以确定行是否以特定字符串开头。|  
|[OffsetToLineNumber](../ide/offsettolinenumber.md)|查找函数体中给定位置的行号。|  
|[OnWizFinish](../ide/onwizfinish.md)|当用户单击“完成”时，从向导 HTML 脚本调用。  调用向导控件的 **Finish** 方法。|  
|[RenderAddTemplate](../ide/renderaddtemplate.md)|呈现模板文件，还可以将其添加到项目中。|  
|[SetCommonPchSettings](../ide/setcommonpchsettings.md)|设置项目的预编译头。|  
|[SetErrorInfo](../ide/seterrorinfo.md)|提供错误信息。|  
|[SetFilters](../ide/setfilters.md)|为项目文件夹添加源、包含和资源筛选器。|  
|[SetMergeProxySymbol](../ide/setmergeproxysymbol.md)|如果需要，则由向导调用以添加 \_MERGE\_PROXYSTUB 符号。|  
|[SetNoPchSettings](../ide/setnopchsettings.md)|当未使用预编译头时，设置项目配置属性。|  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)