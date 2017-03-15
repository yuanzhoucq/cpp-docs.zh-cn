---
title: "CDumpContext 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDumpContext
dev_langs:
- C++
helpviewer_keywords:
- CDumpContext class
- AfxDump object
- diagnostics, diagnostic classes
- diagnostic classes
- diagnosis, diagnostic classes
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 40d833772735e1079647f8f3205fb8db736843fd
ms.lasthandoff: 02/24/2017

---
# <a name="cdumpcontext-class"></a>CDumpContext 类
支持面向流并使用可读文本格式的诊断输出。  
  
## <a name="syntax"></a>语法  
  
```  
class CDumpContext  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDumpContext::CDumpContext](#cdumpcontext)|构造 `CDumpContext` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDumpContext::DumpAsHex](#dumpashex)|转储以十六进制格式的指定的项。|  
|[CDumpContext::Flush](#flush)|刷新转储上下文缓冲区中的任何数据。|  
|[CDumpContext::GetDepth](#getdepth)|获取对应于转储的深度的整数。|  
|[CDumpContext::HexDump](#hexdump)|转储以十六进制格式的一个数组中包含的字节数。|  
|[CDumpContext::SetDepth](#setdepth)|设置转储的深度。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CDumpContext::operator&lt;&lt;](#operator_lt_lt)|转储上下文中插入变量和对象。|  
  
## <a name="remarks"></a>备注  
 `CDumpContext`没有基类的类。  
  
 您可以使用[afxDump](http://msdn.microsoft.com/library/4b3cfa3f-fb75-456a-9d99-a5601acbcb11)，预先声明`CDumpContext`对象，以便您转储的大部分。 `afxDump`对象是仅在 Microsoft 基础类库的调试版本中可用。  
  
 多个内存[诊断服务](../../mfc/reference/diagnostic-services.md)使用`afxDump`其输出。  
  
 在 Windows 环境下从预定义的输出`afxDump`对象，概念上类似于`cerr`流式传输时，会传送到 Windows 函数通过调试器**OutputDebugString**。  
  
 `CDumpContext`类具有重载的插入 ( ** << **) 运算符，用于`CObject`转储对象的数据的指针。 如果您需要自定义转储格式派生的对象，重写[CObject::Dump](../../mfc/reference/cobject-class.md#dump)。 大多数 Microsoft 基础类实现重写`Dump`成员函数。  
  
 不从派生的类`CObject`，如`CString`， `CTime`，和`CTimeSpan`，具有其自己重载`CDumpContext`插入运算符，如经常使用，请执行结构作为**CFileStatus**， `CPoint`，和`CRect`。  
  
 如果您使用[IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic)或[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏在实现您的类，然后`CObject::Dump`将打印的名称您`CObject`的派生类。 否则，该代码会打印`CObject`。  
  
 `CDumpContext`类是可用于调试和发布版本的库，但`Dump`仅在调试版本中定义成员函数。 使用**#ifdef _DEBUG**  /  `#endif`语句来封闭您诊断代码，包括您的自定义`Dump`成员函数。  
  
 创建您自己之前`CDumpContext`对象时，必须创建`CFile`用作转储目标的对象。  
  
 有关详细信息`CDumpContext`，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。  
  
 **#define _DEBUG**  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CDumpContext`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="a-namecdumpcontexta--cdumpcontextcdumpcontext"></a><a name="cdumpcontext"></a>CDumpContext::CDumpContext  
 构造类的对象`CDumpContext`。  
  
```  
CDumpContext(CFile* pFile = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pFile`  
 一个指向`CFile`转储目标的对象。  
  
### <a name="remarks"></a>备注  
 `afxDump`自动构造对象。  
  
 未写入到基础`CFile`活动; 否则为转储上下文时，您将使用该转储磁带。 在 Windows 环境下的输出传送到 Windows 函数通过调试器**OutputDebugString**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&12;](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]  
  
##  <a name="a-namedumpashexa--cdumpcontextdumpashex"></a><a name="dumpashex"></a>CDumpContext::DumpAsHex  
 转储格式化为十六进制数字的指定的类型。  
  
```  
CDumpContext& DumpAsHex(BYTE b);  
CDumpContext& DumpAsHex(DWORD dw);  
CDumpContext& DumpAsHex(int n);  
CDumpContext& DumpAsHex(LONG l);  
CDumpContext& DumpAsHex(LONGLONG n);  
CDumpContext& DumpAsHex(UINT u);  
CDumpContext& DumpAsHex(ULONGLONG n);  
CDumpContext& DumpAsHex(WORD w);
```  
  
### <a name="return-value"></a>返回值  
 对 `CDumpContext` 对象的引用。  
  
### <a name="remarks"></a>备注  
 调用此成员函数来转储为十六进制数的指定类型的项。 若要转储数组，调用[CDumpContext::HexDump](#hexdump)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&13;](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]  
  
##  <a name="a-nameflusha--cdumpcontextflush"></a><a name="flush"></a>CDumpContext::Flush  
 强制缓冲区进行写入到文件中剩余的任何数据附加到转储上下文。  
  
```  
void Flush();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&14;](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]  
  
##  <a name="a-namegetdeptha--cdumpcontextgetdepth"></a><a name="getdepth"></a>CDumpContext::GetDepth  
 确定是否深度或浅表转储为进程中。  
  
```  
int GetDepth() const;  
```  
  
### <a name="return-value"></a>返回值  
 设置的转储的深度`SetDepth`。  
  
### <a name="example"></a>示例  
  请参阅示例[SetDepth](#setdepth)。  
  
##  <a name="a-namehexdumpa--cdumpcontexthexdump"></a><a name="hexdump"></a>CDumpContext::HexDump  
 转储设置为十六进制数字格式的字节数组。  
  
```  
void HexDump(
    LPCTSTR lpszLine,  
    BYTE* pby,  
    int nBytes,  
    int nWidth);
```  
  
### <a name="parameters"></a>参数  
 *lpszLine*  
 要输出的一个新行开头的字符串。  
  
 *pby*  
 指向包含要转储的字节的缓冲区的指针。  
  
 `nBytes`  
 要转储的字节数。  
  
 `nWidth`  
 每行 （不在输出行的宽度） 转储最大字节数。  
  
### <a name="remarks"></a>备注  
 若要转储为十六进制数的单一的特定项类型，调用[CDumpContext::DumpAsHex](#dumpashex)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&15;](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]  
  
##  <a name="a-nameoperatorltlta--cdumpcontextoperator-ltlt"></a><a name="operator_lt_lt"></a>CDumpContext::operator&lt;&lt;  
 将输出转储上下文的指定的数据。  
  
```  
CDumpContext& operator<<(const CObject* pOb);  
CDumpContext& operator<<(const CObject& ob);  
CDumpContext& operator<<(LPCTSTR lpsz);  
CDumpContext& operator<<(const void* lp);  
CDumpContext& operator<<(BYTE by);  
CDumpContext& operator<<(WORD w);  
CDumpContext& operator<<(DWORD dw);  
CDumpContext& operator<<(int n);  
CDumpContext& operator<<(double d);  
CDumpContext& operator<<(float f);  
CDumpContext& operator<<(LONG l);  
CDumpContext& operator<<(UINT u);  
CDumpContext& operator<<(LPCWSTR lpsz);  
CDumpContext& operator<<(LPCSTR lpsz);  
CDumpContext& operator<<(LONGLONG n);  
CDumpContext& operator<<(ULONGLONG n);  
CDumpContext& operator<<(HWND h);  
CDumpContext& operator<<(HDC h);  
CDumpContext& operator<<(HMENU h);  
CDumpContext& operator<<(HACCEL h);  
CDumpContext& operator<<(HFONT h);
```  
  
### <a name="return-value"></a>返回值  
 一个`CDumpContext`引用。 使用返回的值，可以在源代码的一行上编写多个插入操作。  
  
### <a name="remarks"></a>备注  
 为重载插入运算符`CObject`也适用于大多数基元类型的指针。 指向字符的指针将导致转储的字符串内容;一个指向`void`仅的地址的十六进制转储将导致。 一个**LONGLONG**导致 64 位有符号整数; 转储一个**ULONGLONG**导致转储的 64 位无符号整数。  
  
 如果您使用`IMPLEMENT_DYNAMIC`或`IMPLEMENT_SERIAL`宏在实现您的类，然后插入运算符，通过`CObject::Dump`，将打印的名称您`CObject`的派生类。 否则，该代码会打印`CObject`。 如果重写`Dump`函数的类，则可提供更有意义的输出的对象的内容，而不是十六进制转储。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&17;](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]  
  
##  <a name="a-namesetdeptha--cdumpcontextsetdepth"></a><a name="setdepth"></a>CDumpContext::SetDepth  
 设置转储的深度。  
  
```  
void SetDepth(int nNewDepth);
```  
  
### <a name="parameters"></a>参数  
 *nNewDepth*  
 新的深度值。  
  
### <a name="remarks"></a>备注  
 如果要转储的基元类型或简单`CObject`，其中不包含对其他对象的任何指针，则值为 0 就足够了。 大于 0 指定深层转储所有对象的值转储以递归方式。 例如，集合的深层转储将转储集合中的所有元素。 在派生类中，您可以使用其他特定深度值。  
  
> [!NOTE]
>  循环引用在深层转储中未检测到，并且可能会导致无限循环。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&16;](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFile 类](../../mfc/reference/cfile-class.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)

