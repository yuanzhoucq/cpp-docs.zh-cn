---
title: 使用 AFX_EXT_CLASS 导出和导入
ms.date: 11/04/2016
f1_keywords:
- afx_ext_class
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
ms.openlocfilehash: 95c72f8251a8a59833483eb948709c80a69d03d7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328599"
---
# <a name="exporting-and-importing-using-afx_ext_class"></a>使用 AFX_EXT_CLASS 导出和导入

[MFC 扩展 DLL](extension-dlls-overview.md)使用宏**AFX_EXT_CLASS**导出类;链接到 MFC 扩展 DLL 的可执行文件使用宏导入类。 使用**AFX_EXT_CLASS**宏时，用于构建 MFC 扩展名 DLL 的相同标头文件可用于链接到 DLL 的可执行文件。

在 DLL 的标头文件中，将**AFX_EXT_CLASS**关键字添加到类的声明中，如下所示：

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

此宏由 MFC 定义为`__declspec(dllexport)`预处理器符号`_AFXDLL`和`_AFXEXT`定义时。 但是宏定义为`__declspec(dllimport)`何时`_AFXDLL`定义，`_AFXEXT`并且未定义。 定义时，预处理器符号`_AFXDLL`指示目标可执行文件（DLL 或应用程序）正在使用 MFC 的共享版本。 当和`_AFXDLL``_AFXEXT`都定义时，这表示目标可执行文件是 MFC 扩展 DLL。

由于`AFX_EXT_CLASS`定义为从`__declspec(dllexport)`MFC 扩展 DLL 导出时，因此可以导出整个类，而无需在 .def 文件中放置该类的所有符号的修饰名称。

尽管可以避免使用此方法创建 .def 文件和类的所有修饰名称，但创建 .def 文件的效率更高，因为名称可以通过 ddinal 导出。 要使用 .def 文件导出方法，请将以下代码放在标头文件的开头和结尾：

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
> 导出内联函数时要小心，因为它们可能会造成版本冲突。 内联函数将扩展到应用程序代码中;因此，如果以后重写函数，则不会更新该函数，除非重新编译应用程序本身。 通常，DLL 函数可以更新，而无需重新生成使用它们的应用程序。

## <a name="exporting-individual-members-in-a-class"></a>导出类中的单个成员

有时，您可能希望导出类的各个成员。 例如，如果要导出`CDialog`派生类，可能只需要导出构造函数和`DoModal`调用。 您可以在需要导出`AFX_EXT_CLASS`的单个成员上使用。

例如：

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

由于您不再导出类的所有成员，因此由于 MFC 宏的工作方式，可能会遇到其他问题。 MFC 的几个帮助宏实际上声明或定义了数据成员。 因此，这些数据成员也必须从 DLL 导出。

例如，在构建`DECLARE_DYNAMIC`MFC 扩展 DLL 时，宏的定义如下：

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

以静态`AFX_DATA`开头的行是在类内部声明静态对象。 要正确导出此类并从客户端可执行文件访问运行时信息，必须导出此静态对象。 由于静态对象是使用修饰`AFX_DATA`符声明的，因此在构建 DLL`AFX_DATA`时`__declspec(dllexport)`只需定义为 ，并将其定义为构建客户端`__declspec(dllimport)`可执行文件时。 因为`AFX_EXT_CLASS`以这种方式定义，你只需要重新定义`AFX_DATA`，与`AFX_EXT_CLASS`类定义相同。

例如：

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

由于 MFC 始终`AFX_DATA`在其宏中定义的数据项上使用符号，因此此技术适用于所有此类方案。 例如，它适用于`DECLARE_MESSAGE_MAP`。

> [!NOTE]
> 如果要导出整个类而不是类的选定成员，则会自动导出静态数据成员。

### <a name="what-do-you-want-to-do"></a>您希望做什么？

- [使用 .def 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec（出口）从 DLL 导出](exporting-from-a-dll-using-declspec-dllexport.md)

- [导出C++函数，用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [导出 C 函数，用于 C 或C++语言可执行文件](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [修饰名称](reference/decorated-names.md)

- [导入和导出内联函数](importing-and-exporting-inline-functions.md)

- [相互导入](mutual-imports.md)

## <a name="see-also"></a>另请参阅

[从 DLL 导出](exporting-from-a-dll.md)
