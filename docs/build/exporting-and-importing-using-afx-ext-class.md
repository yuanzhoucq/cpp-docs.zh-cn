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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328599"
---
# <a name="exporting-and-importing-using-afx_ext_class"></a>使用 AFX_EXT_CLASS 导出和导入

[MFC 扩展 DLL](extension-dlls-overview.md) 使用宏 AFX_EXT_CLASS  导出类；链接到 MFC 扩展 DLL 的可执行文件使用该宏导入类。 使用 AFX_EXT_CLASS  宏时，用于生成 MFC 扩展 DLL 的相同头文件可以与链接到 DLL 的可执行文件一起使用。

在 DLL 的头文件中，将 AFX_EXT_CLASS  关键字添加到类的声明中，如下所示：

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

在定义预处理器符号 `_AFXDLL` 和 `_AFXEXT` 时，MFC 会将此宏定义为 `__declspec(dllexport)`。 但是当定义 `_AFXDLL` 并且未定义 `_AFXEXT` 时，宏会定义为 `__declspec(dllimport)`。 进行定义时，预处理器符号 `_AFXDLL` 指示目标可执行文件（DLL 或应用程序）在使用 MFC 的共享版本。 当同时定义 `_AFXDLL` 和 `_AFXEXT` 时，这指示目标可执行文件是 MFC 扩展 DLL。

由于在从 MFC 扩展 DLL 导出时，`AFX_EXT_CLASS` 会定义为 `__declspec(dllexport)`，因此可以导出整个类，而无需将该类所有符号的修饰名置于 .def 文件中。

尽管可以使用此方法避免创建 .def 文件和类的所有修饰名，但创建 .def 文件会更高效，因为名称可以按序号导出。 若要使用 .def 文件导出方法，请将以下代码放置在头文件的开头和结尾：

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
> 导出内联函数时要小心，因为它们可能会导致版本冲突。 内联函数会扩展到应用程序代码中；因此，如果以后重写函数，则函数不会更新，除非重新编译应用程序本身。 通常，可以更新 DLL 函数，而无需重新生成使用它们的应用程序。

## <a name="exporting-individual-members-in-a-class"></a>导出类中的单个成员

有时可能要导出类的单个成员。 例如，如果要导出 `CDialog` 派生类，则可能只需要导出构造函数和 `DoModal` 调用。 可以对需要导出的单个成员使用 `AFX_EXT_CLASS`。

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

由于不再导出类的所有成员，因此可能会遇到其他问题，这是因为 MFC 宏的工作方式。 MFC 的一些帮助程序宏实际上声明或定义数据成员。 因此，这些数据成员也必须从 DLL 导出。

例如，在生成 MFC 扩展 DLL 时，`DECLARE_DYNAMIC` 宏会定义如下：

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

以静态 `AFX_DATA` 开头的行会在类的内部声明静态对象。 若要正确导出此类并从客户端可执行文件中访问运行时信息，必须导出此静态对象。 由于静态对象使用修饰符 `AFX_DATA` 进行声明，因此只需在生成 DLL 时将 `AFX_DATA` 定义为 `__declspec(dllexport)`，并在生成客户端可执行文件时将它定义为 `__declspec(dllimport)`。 由于已经以这种方式定义了 `AFX_EXT_CLASS`，因此只需将 `AFX_DATA` 重新定义为与类定义中的 `AFX_EXT_CLASS` 相同。

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

因为 MFC 始终对它在其宏中定义的数据项使用 `AFX_DATA` 符号，所以此方法适用于所有此类方案。 例如，它适用于 `DECLARE_MESSAGE_MAP`。

> [!NOTE]
> 如果要导出整个类，而不是导出类的所选成员，则会自动导出静态数据成员。

### <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用 .def 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec(dllexport) 从 DLL 导出](exporting-from-a-dll-using-declspec-dllexport.md)

- [导出 C++ 函数以用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [导出 C 函数以用于 C 或 C++ 语言可执行文件](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 导入到应用程序中](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [修饰名](reference/decorated-names.md)

- [导入和导出内联函数](importing-and-exporting-inline-functions.md)

- [相互导入](mutual-imports.md)

## <a name="see-also"></a>请参阅

[从 DLL 导出](exporting-from-a-dll.md)
