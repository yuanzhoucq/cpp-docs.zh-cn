---
title: C 多文档模板类
ms.date: 11/04/2016
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
ms.openlocfilehash: 3b3f239b05b1cf7661929333e2d616acce6bedb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319733"
---
# <a name="cmultidoctemplate-class"></a>C 多文档模板类

定义实现多文档界面 (MDI) 的文档模板。

## <a name="syntax"></a>语法

```
class CMultiDocTemplate : public CDocTemplate
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C 多文档模板：C 多文档模板](#cmultidoctemplate)|构造 `CMultiDocTemplate` 对象。|

## <a name="remarks"></a>备注

MDI 应用程序使用主框架窗口作为工作区，用户可以在其中打开零个或多个文档框架窗口，每个窗口都显示一个文档。 有关 MDI 的更详细说明，请参阅*软件设计的 Windows 界面指南*。

文档模板定义三种类型的类之间的关系：

- 从[CDocument](../../mfc/reference/cdocument-class.md)派生的文档类。

- 视图类，它显示来自上面列出的文档类的数据。 可以从[CView](../../mfc/reference/cview-class.md)派生`CScrollView`此类 ，`CFormView`或`CEditView`。 （您也可以直接使用`CEditView`。

- 包含视图的框架窗口类。 对于 MDI 文档模板，可以从 派生此类`CMDIChildWnd`，或者，如果您不需要自定义文档框架窗口的行为，则可以直接使用[CMDIChildWnd，](../../mfc/reference/cmdichildwnd-class.md)而无需派生自己的类。

MDI 应用程序可以支持多种类型的文档，并且不同类型的文档可以同时打开。 应用程序对于它支持的每个文档类型都有一个文档模板。 例如，如果您的 MDI 应用程序同时支持电子表格和文本文档，则应用程序有两`CMultiDocTemplate`个对象。

当用户创建新文档时，应用程序将使用文档模板。 如果应用程序支持多种类型的文档，则框架将从文档模板中获取受支持的文档类型的名称，并在"文件新建"对话框中的列表中显示它们。 用户选择文档类型后，应用程序将创建文档类对象、框架窗口对象和视图对象，并将其附加到彼此。

除了构造函数之外，您不需要调用 的任何`CMultiDocTemplate`成员函数。 框架在内部`CMultiDocTemplate`处理对象。

有关 的详细信息`CMultiDocTemplate`，请参阅[文档模板和文档/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cmultidoctemplatecmultidoctemplate"></a><a name="cmultidoctemplate"></a>C 多文档模板：C 多文档模板

构造 `CMultiDocTemplate` 对象。

```
CMultiDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>参数

*nID资源*<br/>
指定与文档类型一起使用的资源的 ID。 这可能包括菜单、图标、快捷键表和字符串资源。

字符串资源由最多七个子字符串组成，由"\n"字符分隔（如果不包括子字符串，则需要"\n"字符作为占位符;但是，尾随的"\n"字符是不需要的）;这些子字符串描述文档类型。 有关子字符串的信息，请参阅[CDocTemplate：：GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 此字符串资源位于应用程序的资源文件中。 例如：

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

请注意，字符串以"\n"字符开头;这是因为第一个子字符串不用于 MDI 应用程序，因此不包括。 您可以使用字符串编辑器编辑此字符串;但是，使用字符串编辑器可以编辑此字符串。整个字符串在字符串编辑器中显示为单个条目，而不是七个单独的条目。

有关这些资源类型的详细信息，请参阅[资源编辑器](../../windows/resource-editors.md)。

*pDocClass*<br/>
指向文档类`CRuntimeClass`的对象。 此类是您定义的`CDocument`表示文档的派生类。

*pFrame 类*<br/>
指向框架窗口`CRuntimeClass`类的对象。 此类可以是`CMDIChildWnd`派生类，也可以是`CMDIChildWnd`自己的类，如果希望文档框架窗口的默认行为。

*pView 类*<br/>
指向视图类`CRuntimeClass`的对象。 此类是您为`CView`显示文档而定义的派生类。

### <a name="remarks"></a>备注

为应用程序支持的每个`CMultiDocTemplate`文档类型动态分配一个对象，并将每个对象`CWinApp::AddDocTemplate`从应用程序类`InitInstance`的成员函数传递给。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

下面是第二个示例。

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>另请参阅

[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[CSingleDocTemplate 类](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CWinApp 类](../../mfc/reference/cwinapp-class.md)
