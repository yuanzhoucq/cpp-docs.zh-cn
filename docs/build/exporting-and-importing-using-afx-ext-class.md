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
ms.openlocfilehash: bcfdc94e8db80daec227d77c20ecec6b14d5af11
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821217"
---
# <a name="exporting-and-importing-using-afxextclass"></a>使用 AFX_EXT_CLASS 导出和导入

[MFC 扩展 Dll](extension-dlls-overview.md)使用宏**AFX_EXT_CLASS**要导出的类; 链接到 MFC 扩展 DLL 的可执行文件使用宏来导入类。 与**AFX_EXT_CLASS**宏，用于生成 MFC 扩展 DLL 可用于链接到 DLL 的可执行文件的同一个标头文件。

在您的 DLL 的标头文件，添加**AFX_EXT_CLASS**关键字到您的类的声明，如下所示：

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

作为 mfc 定义此宏`__declspec(dllexport)`时预处理器符号`_AFXDLL`和`_AFXEXT`定义。 但该宏指`__declspec(dllimport)`时`_AFXDLL`定义和`_AFXEXT`未定义。 在定义时，预处理器符号`_AFXDLL`指示共享的版本的 MFC 正由目标可执行文件 （DLL 或应用程序）。 当同时`_AFXDLL`和`_AFXEXT`是定义，这表示目标可执行文件是 MFC 扩展 DLL。

因为`AFX_EXT_CLASS`定义为`__declspec(dllexport)`时从 MFC 扩展 DLL 中导出，你可以导出整个类，而无需将所有此类符号的修饰的名放到.def 文件中。

尽管您可以避免使用此方法创建一个.def 文件与所有类的修饰名，请创建一个.def 文件更高效是因为可以按序号导出名称。 若要使用.def 文件导出方法，请在开头和末尾标头文件放置以下代码：

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
>  时要小心导出内联函数，因为他们可以创建版本冲突的可能性。 内联函数获取扩展为应用程序代码;因此，如果您更高版本重写函数，它不会更新除非重新编译应用程序本身。 通常情况下，DLL 函数可以更新而重新生成的应用程序使用它们。

## <a name="exporting-individual-members-in-a-class"></a>导出类中的各个成员

有时你可能想要导出类中的单个成员。 例如，如果要导出`CDialog`的派生的类，您可能只需要导出该构造函数和`DoModal`调用。 可以使用`AFX_EXT_CLASS`需要导出单个成员上。

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

无法再导出类的所有成员，因为您可能会遇到另一个问题由于的方式 MFC 宏的工作。 MFC 的帮助器宏的几个实际声明或定义数据成员。 因此，还必须从 DLL 导出这些成员。

例如，`DECLARE_DYNAMIC`生成 MFC 扩展 DLL 时，如下所示定义宏：

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

以具有静态行`AFX_DATA`声明内您的类的静态对象。 若要正确进行导出此类并从客户端可执行文件访问运行时信息，则必须导出此静态对象。 因为使用修饰符声明的静态对象`AFX_DATA`，只需定义`AFX_DATA`要`__declspec(dllexport)`生成 DLL 时并将其作为定义`__declspec(dllimport)`生成客户端可执行文件时。 因为`AFX_EXT_CLASS`已定义这种方式，只需重新定义`AFX_DATA`是与相同`AFX_EXT_CLASS`围绕你的类定义。

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

因为始终使用 MFC`AFX_DATA`它定义了其中的宏中的数据项上这种情况下此技术是有效的符号。 例如，它适用于`DECLARE_MESSAGE_MAP`。

> [!NOTE]
>  如果要导出整个类而不是所选的成员的类，静态数据成员将自动导出。

### <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用.def 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport） 从 DLL 导出](exporting-from-a-dll-using-declspec-dllexport.md)

- [导出 c + + 函数以用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [导出 C 函数以用于 C 或 c + + 语言可执行文件](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [导入到使用 __declspec （dllimport） 的应用程序](importing-into-an-application-using-declspec-dllimport.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [修饰的名](reference/decorated-names.md)

- [导入和导出内联函数](importing-and-exporting-inline-functions.md)

- [相互导入](mutual-imports.md)

## <a name="see-also"></a>请参阅

[从 DLL 导出](exporting-from-a-dll.md)
