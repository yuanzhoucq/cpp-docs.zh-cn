---
title: CSingleDocTemplate 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
dev_langs:
- C++
helpviewer_keywords:
- CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
author: mikeblome
ms.author: mblome
ms.openlocfilehash: ea133213b8d1d91a6c0932c7f0b7a94c5d5a368a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026760"
---
# <a name="csingledoctemplate-class"></a>CSingleDocTemplate 类
定义实现单文档界面 (SDI) 的文档模板。  
  
## <a name="syntax"></a>语法  
  
```  
class CSingleDocTemplate : public CDocTemplate  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSingleDocTemplate::CSingleDocTemplate](#csingledoctemplate)|构造 `CSingleDocTemplate` 对象。|  
  
## <a name="remarks"></a>备注  
 SDI 应用程序使用主框架窗口显示文档;一次只有一个文档可以是打开的。  
  
 文档模板定义了三种类型的类之间的关系：  
  
-   文档类，派生自`CDocument`。  
  
-   视图类，该类显示上面列出的文档类中的数据。 可以派生此类从`CView`， `CScrollView`， `CFormView`，或`CEditView`。 (还可以使用`CEditView`直接。)  
  
-   框架窗口类，包含的视图。 对于 SDI 文档模板，可以派生此类从`CFrameWnd`; 如果不需要自定义行为的主框架窗口中，可以使用`CFrameWnd`不直接派生您自己的类。  
  
 SDI 应用程序通常支持一种类型的文档，因此它只有一个`CSingleDocTemplate`对象。 一次只有一个文档可以是打开的。  
  
 无需调用的函数的任何成员`CSingleDocTemplate`除外构造函数。 Framework 句柄`CSingleDocTemplate`内部对象。  
  
 有关使用的详细信息`CSingleDocTemplate`，请参阅[文档模板和文档/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CSingleDocTemplate`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="csingledoctemplate"></a>  CSingleDocTemplate::CSingleDocTemplate  
 构造 `CSingleDocTemplate` 对象。  
  
```  
CSingleDocTemplate(
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>参数  
 *nIDResource*  
 指定与文档类型一起使用的资源 ID。 这可能包括菜单、 图标、 快捷键对应表和字符串资源。  
  
 字符串资源都包括最多七个 \n 字符分隔的子字符串 （'\n' 字符需要作为占位符，如果子字符串未包含; 但是，不需要尾随的 '\n' 字符）;这些子字符串描述文档类型。 有关子字符串的信息，请参阅[CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 应用程序的资源文件中找到此字符串资源。 例如：  
  
```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"
END
```
  
 您可以编辑此字符串使用字符串编辑器;整个字符串不为七个不同的项作为单个条目在字符串编辑器中，将出现。  
  
 有关这些资源类型的详细信息，请参阅[字符串编辑器](../../windows/string-editor.md)。  
  
 *pDocClass*  
 指向`CRuntimeClass`文档类的对象。 此类是`CDocument`-派生的类定义来表示你的文档。  
  
 *pFrameClass*  
 指向`CRuntimeClass`框架窗口类的对象。 此类可以是`CFrameWnd`的派生的类，也可以是`CFrameWnd`本身如果你希望用于您的主框架窗口的默认行为。  
  
 *pViewClass*  
 指向`CRuntimeClass`视图类的对象。 此类是`CView`-派生的类定义以显示你的文档。  
  
### <a name="remarks"></a>备注  
 动态分配`CSingleDocTemplate`对象，并将其传递给`CWinApp::AddDocTemplate`从`InitInstance`的应用程序类的成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 DOCKTOOL](../../visual-cpp-samples.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument 类](../../mfc/reference/cdocument-class.md)   
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)   
 [CMultiDocTemplate 类](../../mfc/reference/cmultidoctemplate-class.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CWinApp 类](../../mfc/reference/cwinapp-class.md)
