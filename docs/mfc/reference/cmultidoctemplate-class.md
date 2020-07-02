---
title: CMultiDocTemplate 类
ms.date: 11/04/2016
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
ms.openlocfilehash: af950d188c4e02a38a39ed3c672f0f8c4161bee8
ms.sourcegitcommit: 8fd49f8ac20457710ceb5403ca46fc73cb3f95f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737477"
---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate 类

定义实现多文档界面 (MDI) 的文档模板。

## <a name="syntax"></a>语法

```
class CMultiDocTemplate : public CDocTemplate
```

## <a name="members"></a>成员

此类的成员函数是虚拟的。 有关文档，请参阅[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)和[CCmdTarget](../../mfc/reference/ccmdtarget-class.md) 。

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|构造 `CMultiDocTemplate` 对象。|

## <a name="remarks"></a>备注

MDI 应用程序使用主框架窗口作为工作区，用户可以在其中打开零个或多个文档框架窗口，其中每个窗口都显示一个文档。 有关 MDI 的更详细说明，请参阅*软件设计的 Windows 界面指导原则*。

文档模板定义了三种类型的类之间的关系：

- 一个从[CDocument](../../mfc/reference/cdocument-class.md)派生的文档类。

- 视图类，用于显示上面列出的文档类中的数据。 可以从[CView](../../mfc/reference/cview-class.md)、、或派生此 `CScrollView` 类 `CFormView` `CEditView` 。 （也可以直接使用 `CEditView` 。）

- 包含视图的框架窗口类。 对于 MDI 文档模板，你可以从派生此类 `CMDIChildWnd` ，如果不需要自定义文档框架窗口的行为，则可以直接使用[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) ，而无需派生你自己的类。

MDI 应用程序可以支持多种类型的文档，并且可以同时打开不同类型的文档。 应用程序为其支持的每个文档类型都有一个文档模板。 例如，如果您的 MDI 应用程序同时支持电子表格和文本文档，则该应用程序有两个 `CMultiDocTemplate` 对象。

当用户创建新文档时，应用程序将使用文档模板。 如果应用程序支持多种类型的文档，则框架将从文档模板获取支持的文档类型的名称，并在 "文件" "新建" 对话框的列表中显示它们。 用户选择了文档类型后，该应用程序将创建一个文档类对象、一个框架窗口对象和一个视图对象，然后将它们彼此连接。

不需要调用 `CMultiDocTemplate` 除构造函数之外的任何成员函数。 框架 `CMultiDocTemplate` 在内部处理对象。

有关的详细信息 `CMultiDocTemplate` ，请参阅[文档模板和文档/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cmultidoctemplatecmultidoctemplate"></a><a name="cmultidoctemplate"></a>CMultiDocTemplate::CMultiDocTemplate

构造 `CMultiDocTemplate` 对象。

```
CMultiDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>参数

*nIDResource*<br/>
指定用于文档类型的资源的 ID。 这可能包括菜单、图标、快捷键对应表和字符串资源。

String 资源包含由 "\n" 字符分隔的最多七个子字符串（如果不包含子字符串，则需要使用 "\n" 字符作为占位符，但不需要后缀 "\n" 字符）;这些子字符串说明了文档类型。 有关子字符串的信息，请参阅[CDocTemplate：： GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 此字符串资源位于应用程序的资源文件中。 例如：

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

字符串以 "\n" 字符开头，因为第一个子字符串不用于 MDI 应用程序，因此不包括在内。 您可以使用字符串编辑器来编辑此字符串;整个字符串在字符串编辑器中显示为一个条目，而不是作为7个单独的条目。

有关这些资源类型的详细信息，请参阅[资源编辑器](../../windows/resource-editors.md)。

*pDocClass*<br/>
指向 `CRuntimeClass` document 类的对象。 此类是一个 `CDocument` 派生类，可以定义它来表示文档。

*pFrameClass*<br/>
指向 `CRuntimeClass` 框架窗口类的对象。 此类可以是 `CMDIChildWnd` 派生类，也可以是 `CMDIChildWnd` 您的文档框架窗口的默认行为。

*pViewClass*<br/>
指向 `CRuntimeClass` 视图类的对象。 此类是一个 `CView` 派生类，可以定义它以显示文档。

### <a name="remarks"></a>备注

`CMultiDocTemplate`对于应用程序支持的每个文档类型，动态分配一个对象，并将每个对象 `CWinApp::AddDocTemplate` 从 `InitInstance` 应用程序类的成员函数传递到其中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

下面是第二个示例。

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>请参阅

[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[CSingleDocTemplate 类](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CWinApp 类](../../mfc/reference/cwinapp-class.md)
