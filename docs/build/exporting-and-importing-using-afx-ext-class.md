---
title: "导出和导入使用 AFX_EXT_CLASS |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: afx_ext_class
dev_langs: C++
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 753395713bd4831f1dbc55403134898ae68ca182
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="exporting-and-importing-using-afxextclass"></a>使用 AFX_EXT_CLASS 导出和导入  
  
[MFC 扩展 Dll](../build/extension-dlls-overview.md)使用宏**AFX_EXT_CLASS**导出类; 链接到 MFC 扩展 DLL 的可执行文件使用宏来导入类。 与**AFX_EXT_CLASS**宏，用于生成 MFC 扩展 DLL 可以用于链接到 DLL 的可执行文件的同一个标头文件。  
  
 在为 DLL 标头文件中，添加**AFX_EXT_CLASS**到你的类，如下所示的声明的关键字：  
  
```cpp  
class AFX_EXT_CLASS CMyClass : public CDocument  
{  
// <body of class>  
};  
```  
  
作为 mfc 定义此宏`__declspec(dllexport)`时预处理器符号`_AFXDLL`和`_AFXEXT`定义。 但宏定义为`__declspec(dllimport)`时`_AFXDLL`定义和`_AFXEXT`未定义。 在定义时，预处理器符号`_AFXDLL`指示共享的版本的 MFC 正在由目标可执行文件 （DLL 或应用程序）。 当同时`_AFXDLL`和`_AFXEXT`是定义，这表示目标可执行文件是 MFC 扩展 DLL。  
  
因为`AFX_EXT_CLASS`定义为`__declspec(dllexport)`时从 MFC 扩展 DLL 中导出，你可以导出整个类，而无需将所有此类符号的修饰的名放入.def 文件。  
  
因为名称可以按序号导出，尽管你可以避免使用此方法创建一个.def 文件和所有类的修饰名，创建一个.def 文件会更加高效。 若要使用.def 文件导出方法，请在起点和标头文件的末尾将以下代码：  
  
```cpp  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
> [!CAUTION]
>  时要小心导出内联函数，因为他们可以创建的版本冲突的可能性。 内联函数获取扩展到了应用程序代码中;因此，如果您更高版本重写函数，它未更新除非重新编译应用程序本身。 通常，DLL 函数可以更新而重新生成的应用程序使用它们。  
  
## <a name="exporting-individual-members-in-a-class"></a>导出类中的各个成员  
  
有时你可能想要导出你的类的个别成员。 例如，如果要导出`CDialog`-派生类中，你可能只需导出构造函数和`DoModal`调用。 你可以使用`AFX_EXT_CLASS`您需要将导出单个成员上。  
  
例如:   
  
```cpp  
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
  
因为你无法再导出类的所有成员，你可能会遇到其他问题由于 MFC 宏的工作。 MFC 的帮助器宏多种实际声明或定义数据成员。 因此，还必须从 DLL 导出这些数据成员。  
  
例如，`DECLARE_DYNAMIC`生成 MFC 扩展 DLL 时，如下所示定义宏：  
  
```cpp  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
   static CRuntimeClass* PASCAL _GetBaseClass(); \  
public: \  
   static AFX_DATA CRuntimeClass class##class_name; \  
   virtual CRuntimeClass* GetRuntimeClass() const; \  
```  
  
开头静态行`AFX_DATA`声明内您的类的静态对象。 若要正确进行导出此类，并从客户端可执行文件访问运行时信息，你必须导出此静态对象。 因为使用修饰符声明的静态对象`AFX_DATA`，只需定义`AFX_DATA`要`__declspec(dllexport)`时生成您的 DLL 并将其作为定义`__declspec(dllimport)`生成你的客户端可执行文件时。 因为`AFX_EXT_CLASS`已定义这种方式，你只需重新定义`AFX_DATA`会作为相同`AFX_EXT_CLASS`解决你的类定义。  
  
例如:   
  
```cpp  
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
  
因为 MFC 始终使用`AFX_DATA`符号在它定义其中的宏中的数据项上此方法适用于所有此类方案。 例如，它适用于`DECLARE_MESSAGE_MAP`。  
  
> [!NOTE]
>  如果你要导出整个类而不是所选的类的成员，将自动导出静态数据成员。  
  
### <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [使用.def 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [导出 C 语言可执行文件中使用的 c + + 函数](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [在 C 或 c + + 语言可执行文件中使用的导出 C 函数](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [导入使用 __declspec （dllimport） 的应用程序](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [修饰的名](../build/reference/decorated-names.md)  
  
-   [导入和导出内联函数](../build/importing-and-exporting-inline-functions.md)  
  
-   [相互导入](../build/mutual-imports.md)  
  
## <a name="see-also"></a>另请参阅  
 [从 DLL 导出](../build/exporting-from-a-dll.md)