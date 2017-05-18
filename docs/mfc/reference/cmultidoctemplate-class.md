---
title: "CMultiDocTemplate 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
dev_langs:
- C++
helpviewer_keywords:
- MDI, template
- CMultiDocTemplate class
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 6e58325cd4dcaec01bf8a76006bb397fccd9a171
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmultidoctemplate-class"></a>CMultiDocTemplate 类
定义实现多文档界面 (MDI) 的文档模板。  
  
## <a name="syntax"></a>语法  
  
```  
class CMultiDocTemplate : public CDocTemplate  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|构造 `CMultiDocTemplate` 对象。|  
  
## <a name="remarks"></a>备注  
 MDI 应用程序中使用作为工作区中，用户可以在其中打开了零个或多个文档框架窗口，其中每个显示文档的主框架窗口。 MDI 的更多详细说明，请参阅*软件设计的 Windows 界面指南*。  
  
 文档模板定义了三种类型的类之间的关系︰  
  
-   一个文档类，该类派生自[CDocument](../../mfc/reference/cdocument-class.md)。  
  
-   视图类，该类显示上面列出的文档类中的数据。 可派生自此类，从[CView](../../mfc/reference/cview-class.md)， `CScrollView`， `CFormView`，或`CEditView`。 (您还可以使用`CEditView`直接。)  
  
-   框架窗口类，包含的视图。 对于 MDI 文档模板，可以派生自此类，从`CMDIChildWnd`，或者，如果您不需要自定义文档框架窗口的行为，可以使用[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)直接而不用派生您自己的类。  
  
 MDI 应用程序可以支持多个类型的文档，并且可以同时打开不同类型的文档。 应用程序具有它支持每种文档类型的一个文档模板。 例如，如果 MDI 应用程序支持电子表格和文本文档，该应用程序有两个`CMultiDocTemplate`对象。  
  
 当用户创建一个新文档时，应用程序使用的文档模板。 如果应用程序支持多个类型的文档，框架从文档模板中获取受支持的文档类型的名称，并将它们显示在文件新建对话框中的列表。 一旦在用户已经选择一种文档类型，该应用程序创建文档类对象、 框架窗口对象和视图对象，并将其附加到每个其他。  
  
 不需要调用的函数的任何成员`CMultiDocTemplate`除外构造函数。 Framework 句柄`CMultiDocTemplate`内部对象。  
  
 有关详细信息`CMultiDocTemplate`，请参阅[文档模板和文档/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CMultiDocTemplate`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cmultidoctemplate"></a>CMultiDocTemplate::CMultiDocTemplate  
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
  
 字符串资源都包括达七个 \n 字符分隔的子字符串 （'\n' 字符需要作为一个占位符，不含一个子字符串时; 但是，不需要尾随的 '\n' 字符）;这些子字符串说明了文档类型。 子字符串的信息，请参阅[CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 应用程序的资源文件中可以找到该字符串资源。 例如:   
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 请注意，该字符串开头的 '\n' 字符;这是因为第一个子字符串不用于 MDI 应用程序，因此不包括在内。 您可以编辑使用字符串编辑器; 此字符串整个字符串不是作为七个不同的项作为单个条目在字符串编辑器中，将出现。  
  
 有关这些资源类型的详细信息，请参阅[资源编辑器](../../windows/resource-editors.md)。  
  
 `pDocClass`  
 指向`CRuntimeClass`文档类的对象。 此类是**CDocument**的派生类定义来表示你的文档。  
  
 `pFrameClass`  
 指向`CRuntimeClass`框架窗口类的对象。 此类可以是`CMDIChildWnd`-派生的类，也可以是`CMDIChildWnd`本身如果你希望用于你的文档框架窗口的默认行为。  
  
 `pViewClass`  
 指向`CRuntimeClass`视图类的对象。 此类是`CView`的派生类定义以显示您的文档。  
  
### <a name="remarks"></a>备注  
 动态分配一个`CMultiDocTemplate`每个文档类型，您的应用程序支持，并将传递到每个对象`CWinApp::AddDocTemplate`从`InitInstance`应用程序类的成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&92;](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]  
  
 下面是第二个示例。  
  
 [!code-cpp[NVC_MFCDocView #&93;](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)   
 [CSingleDocTemplate 类](../../mfc/reference/csingledoctemplate-class.md)   
 [CWinApp 类](../../mfc/reference/cwinapp-class.md)

