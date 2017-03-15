---
title: "使用 AFX_EXT_CLASS 导出和导入 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "afx_ext_class"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFX_EXT_CLASS 宏"
  - "可执行文件 [C++], 导入类"
  - "导出类 [C++]"
  - "导出 DLL [C++], AFX_EXT_CLASS 宏"
  - "扩展 DLL [C++], 导出类"
  - "导入 DLL [C++]"
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用 AFX_EXT_CLASS 导出和导入
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[扩展 DLL](../build/extension-dlls-overview.md) 使用 **AFX\_EXT\_CLASS** 宏导出类；链接到扩展 DLL 的可执行文件使用该宏导入类。  用于生成扩展 DLL 的相同头文件可通过 **AFX\_EXT\_CLASS** 宏与链接到 DLL 的可执行文件一起使用。  
  
 在 DLL 的头文件中，将 **AFX\_EXT\_CLASS** 关键字添加到类的声明中，如下所示：  
  
```  
class AFX_EXT_CLASS CMyClass : public CDocument  
{  
// <body of class>  
};  
```  
  
 当定义了预处理器符号 **\_AFXDLL** 和 `_AFXEXT` 时，该宏被 MFC 定义为 **\_\_declspec\(dllexport\)**。  但当定义了 **\_AFXDLL** 而未定义 `_AFXEXT` 时，该宏被定义为 **\_\_declspec\(dllimport\)**。  定义后，预处理器符号 **\_AFXDLL** 指示共享 MFC 版本正在由目标可执行文件（DLL 或应用程序）使用。  当 **\_AFXDLL** 和 `_AFXEXT` 都定义了时，这指示目标可执行文件是扩展 DLL。  
  
 由于从扩展 DLL 导出时，**AFX\_EXT\_CLASS** 被定义为 **\_\_declspec\(dllexport\)**，因此可以导出整个类，而不必将该类的所有符号的修饰名放到 .def 文件中。  此方法由 MFC 示例 [DLLHUSK](http://msdn.microsoft.com/zh-cn/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) 使用。  
  
 虽然使用此方法可以避免创建 .def 文件和类的所有修饰名，但由于名称可以按序号导出，因此创建 .def 文件的效率更高。  若要使用 .def 文件导出方法，请将下列代码放在头文件的开头和结尾处：  
  
```  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
> [!CAUTION]
>  导出内联函数时要小心，因为它们有可能导致版本冲突。  内联函数扩展到应用程序代码中；因此，如果以后重写内联函数，除非重新编译应用程序本身，否则内联函数不会被更新。  通常，不用重新生成使用 DLL 函数的应用程序就可以更新 DLL 函数。  
  
## 导出类中的个别成员  
 有时，您可能希望导出类中的个别成员。  例如，如果导出 `CDialog` 派生类，可能只需要导出构造函数和 `DoModal` 调用。  可以对需要导出的个别成员使用 **AFX\_EXT\_CLASS**。  
  
 例如：  
  
```  
class CExampleDialog : public CDialog  
{  
public:  
   AFX_EXT_CLASS CExampleDialog();  
   AFX_EXT_CLASS int DoModal();  
   ...  
   // rest of class definition  
   ...  
};  
```  
  
 您不再导出类的所有成员，但由于 MFC 宏的工作方式，您可能会遇到其他问题。  几个 MFC 的 Helper 宏实际声明或定义数据成员。  因此，还必须从 DLL 导出这些数据成员。  
  
 例如，当生成扩展 DLL 时，`DECLARE_DYNAMIC` 宏的定义如下：  
  
```  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
   static CRuntimeClass* PASCAL _GetBaseClass(); \  
public: \  
   static AFX_DATA CRuntimeClass class##class_name; \  
   virtual CRuntimeClass* GetRuntimeClass() const; \  
```  
  
 以 static `AFX_DATA` 打头的行声明类的内部静态对象。  若要正确导出该类并从客户端可执行文件访问运行时信息，必须导出此静态对象。  由于静态对象是用 `AFX_DATA` 修饰符声明的，因此只需在生成 DLL 时将 `AFX_DATA` 定义为 **\_\_declspec\(dllexport\)**，在生成客户端可执行文件时将其定义为 **\_\_declspec\(dllimport\)**。  由于已经以此方式定义了 **AFX\_EXT\_CLASS**，因此只需参考类定义，将 `AFX_DATA` 重定义为与 **AFX\_EXT\_CLASS** 相同。  
  
 例如：  
  
```  
#undef  AFX_DATA  
#define AFX_DATA AFX_EXT_CLASS  
  
class CExampleView : public CView  
{  
   DECLARE_DYNAMIC()  
   // ... class definition ...  
};  
  
#undef  AFX_DATA  
#define AFX_DATA  
```  
  
 MFC 总是在其宏的内部定义的数据项上使用 `AFX_DATA` 符号，因此此技术适用于所有这类情况。  例如，它适用于 `DECLARE_MESSAGE_MAP`。  
  
> [!NOTE]
>  如果导出整个类而非选定的类成员，静态数据成员将自动导出。  
  
### 你希望做什么？  
  
-   [使用 .def 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [导出 C\+\+ 函数以用于 C 语言可执行文件](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [导出 C 函数以用于 C 或 C\+\+ 语言可执行文件](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [使用 \_\_declspec\(dllimport\) 导入到应用程序中](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
### 您想进一步了解什么？  
  
-   [修饰名](../build/reference/decorated-names.md)  
  
-   [导入和导出内联函数](../build/importing-and-exporting-inline-functions.md)  
  
-   [相互导入](../build/mutual-imports.md)  
  
## 请参阅  
 [从 DLL 导出](../build/exporting-from-a-dll.md)