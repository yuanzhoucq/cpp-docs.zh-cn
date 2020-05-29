---
title: CSingleDocTemplate 类
ms.date: 11/04/2016
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
helpviewer_keywords:
- CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
ms.openlocfilehash: 5a014b35a6cd2d12367e190e4d6dd689e28eae66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318346"
---
# <a name="csingledoctemplate-class"></a>CSingleDocTemplate 类

定义实现单文档界面 (SDI) 的文档模板。

## <a name="syntax"></a>语法

```
class CSingleDocTemplate : public CDocTemplate
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CSingleDoc模板：C单文档模板](#csingledoctemplate)|构造 `CSingleDocTemplate` 对象。|

## <a name="remarks"></a>备注

SDI 应用程序使用主框架窗口来显示文档;一次只能打开一个文档。

文档模板定义三种类型的类之间的关系：

- 从 派生的文档`CDocument`类。

- 视图类，它显示来自上面列出的文档类的数据。 可以从`CView`派生此类，`CScrollView`或`CFormView`。 `CEditView` （您也可以直接使用`CEditView`。

- 包含视图的框架窗口类。 对于 SDI 文档模板，可以从 派生`CFrameWnd`此类。如果不需要自定义主框架窗口的行为，则可以直接使用`CFrameWnd`，而无需派生自己的类。

SDI 应用程序通常支持一种类型的文档，因此它只有一个`CSingleDocTemplate`对象。 一次只能打开一个文档。

除了构造函数之外，您不需要调用 的任何`CSingleDocTemplate`成员函数。 框架在内部`CSingleDocTemplate`处理对象。

有关 使用`CSingleDocTemplate`的详细信息，请参阅[文档模板和文档/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CSingleDocTemplate`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="csingledoctemplatecsingledoctemplate"></a><a name="csingledoctemplate"></a>CSingleDoc模板：C单文档模板

构造 `CSingleDocTemplate` 对象。

```
CSingleDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>参数

*nID资源*<br/>
指定与文档类型一起使用的资源的 ID。 这可能包括菜单、图标、快捷键表和字符串资源。

字符串资源由最多七个子字符串组成，由"\n"字符分隔（如果未包含子字符串，则需要"\n"字符作为占位符;但是，尾随的"\n"字符是不需要的）;这些子字符串描述文档类型。 有关子字符串的信息，请参阅[CDocTemplate：：GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 此字符串资源位于应用程序的资源文件中。 例如：

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"
END
```

您可以使用字符串编辑器编辑此字符串;但是，使用字符串编辑器可以编辑此字符串。整个字符串在字符串编辑器中显示为单个条目，而不是七个单独的条目。

有关这些资源类型的详细信息，请参阅[字符串编辑器](../../windows/string-editor.md)。

*pDocClass*<br/>
指向文档类`CRuntimeClass`的对象。 此类是您定义的`CDocument`表示文档的派生类。

*pFrame 类*<br/>
指向框架窗口`CRuntimeClass`类的对象。 类可以是`CFrameWnd`派生类，也可以是`CFrameWnd`自己的，如果您想要主框架窗口的默认行为。

*pView 类*<br/>
指向视图类`CRuntimeClass`的对象。 此类是您为`CView`显示文档而定义的派生类。

### <a name="remarks"></a>备注

动态分配`CSingleDocTemplate`对象，并将其`CWinApp::AddDocTemplate`从应用程序类`InitInstance`的成员函数传递给对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]

[!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品对接](../../overview/visual-cpp-samples.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument 类](../../mfc/reference/cdocument-class.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[C 多文档模板类](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)<br/>
[CWinApp 类](../../mfc/reference/cwinapp-class.md)
