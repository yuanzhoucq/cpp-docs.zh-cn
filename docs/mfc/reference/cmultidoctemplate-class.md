---
title: CMultiDocTemplate 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
dev_langs:
- C++
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b53228b6983c0293eb288cd0f38669d1b5db928
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371577"
---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate 类
定义实现多文档界面 (MDI) 的文档模板。  
  
## <a name="syntax"></a>语法  
  
```  
class CMultiDocTemplate : public CDocTemplate  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|构造 `CMultiDocTemplate` 对象。|  
  
## <a name="remarks"></a>备注  
 MDI 应用程序使用工作区中，用户可以在其中打开了零个或多个文档框架窗口，其中每个显示文档作为主框架窗口。 MDI 的更多详细说明，请参阅*软件设计的 Windows 界面指南*。  
  
 文档模板定义了三种类型的类之间的关系：  
  
-   文档类，该类派生自[CDocument](../../mfc/reference/cdocument-class.md)。  
  
-   视图类，它显示从上面列出的文档类的数据。 可以派生此类从[CView](../../mfc/reference/cview-class.md)， `CScrollView`， `CFormView`，或`CEditView`。 (你还可以使用`CEditView`直接。)  
  
-   框架窗口类，包含的视图。 MDI 文档模板，可以派生此类从`CMDIChildWnd`，或者，如果你不需要自定义文档框架窗口的行为，可以使用[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)直接而不用派生您自己的类。  
  
 MDI 应用程序可以支持多个类型的文档，并且可以同时打开不同类型的文档。 你的应用程序具有它支持每个文档类型的一个文档模板。 例如，如果 MDI 应用程序支持电子表格和文本文档，该应用程序具有两个`CMultiDocTemplate`对象。  
  
 当用户创建新文档，该应用程序使用的文档模板。 如果应用程序支持多个类型的文档，框架中的文档模板获取支持的文档类型的名称，并将它们显示在新建文件对话框中的列表。 一旦用户选定的文档类型，应用程序创建的文档类对象、 框架窗口对象和视图对象，并将其附加到每个其他。  
  
 不需要调用任何成员函数`CMultiDocTemplate`除外构造函数。 Framework 句柄`CMultiDocTemplate`内部对象。  
  
 有关详细信息`CMultiDocTemplate`，请参阅[文档模板和文档/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CMultiDocTemplate`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cmultidoctemplate"></a>  CMultiDocTemplate::CMultiDocTemplate  
 构造 `CMultiDocTemplate` 对象。  
  
```  
CMultiDocTemplate(
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>参数  
 `nIDResource`  
 指定与文档类型一起使用的资源的 ID。 这可能包括菜单、 图标、 快捷键对应表和字符串资源。  
  
 字符串资源包含最多七由 \n 字符分隔的子字符串 （不包括子字符串时，需要将 \n 字符作为一个占位符; 但是，不需要尾随 \n 字符）;这些子字符串描述文档类型。 子字符串的信息，请参阅[CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 在应用程序的资源文件中找到此字符串资源。 例如：  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 请注意，字符串开始使用 \n 的字符;这是因为第一个子字符串不用于 MDI 应用程序，因此不包括。 你可以编辑使用字符串编辑器中; 此字符串整个字符串会作为单个条目在字符串编辑器中，会出现不为七个不同的项。  
  
 有关这些资源类型的详细信息，请参阅[资源编辑器](../../windows/resource-editors.md)。  
  
 `pDocClass`  
 指向`CRuntimeClass`文档类的对象。 此类是**CDocument**-派生类，定义来表示你的文档。  
  
 `pFrameClass`  
 指向`CRuntimeClass`框架窗口类的对象。 此类可以是`CMDIChildWnd`-派生类，也可以是`CMDIChildWnd`本身如果你希望用于你的文档框架窗口的默认行为。  
  
 `pViewClass`  
 指向`CRuntimeClass`视图类的对象。 此类是`CView`-派生类定义以显示你的文档。  
  
### <a name="remarks"></a>备注  
 动态分配一个`CMultiDocTemplate`每个文档类型，你的应用程序支持，并将传递到每个对象`CWinApp::AddDocTemplate`从`InitInstance`的应用程序类的成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]  
  
 下面是第二个示例。  
  
 [!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)   
 [CSingleDocTemplate 类](../../mfc/reference/csingledoctemplate-class.md)   
 [CWinApp 类](../../mfc/reference/cwinapp-class.md)
