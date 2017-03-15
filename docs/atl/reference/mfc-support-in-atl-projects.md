---
title: "ATL 项目中的 MFC 支持 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.atl.addmfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 项目, MFC 支持"
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# ATL 项目中的 MFC 支持
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果在 ATL 项目向导中选择“支持 MFC”，则项目将应用程序声明为 MFC 应用程序对象（类）。  项目初始化 MFC 库并实例化从 [CWinApp](../../mfc/reference/cwinapp-class.md) 导出的类（*ProjName* 类）。  
  
 此选项仅适用于非特性化 ATL DLL 项目。  
  
```  
class CProjNameApp : public CWinApp  
{  
public:  
  
// Overrides  
   virtual BOOL InitInstance();  
   virtual int ExitInstance();  
   DECLARE_MESSAGE_MAP()  
};  
  
BEGIN_MESSAGE_MAP(CProjNameApp, CWinApp)  
END_MESSAGE_MAP()  
  
CProjNameApp theApp;  
  
BOOL CProjNameApp::InitInstance()  
{  
   return CWinApp::InitInstance();  
}  
  
int CProjNameApp::ExitInstance()  
{  
   return CWinApp::ExitInstance();  
}  
```  
  
 可以在类视图中查看应用程序对象类及其 `InitInstance` 和 `ExitInstance` 函数。  
  
## 请参阅  
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)