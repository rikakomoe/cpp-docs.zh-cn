---
title: COleDispatchException 类
ms.date: 11/04/2016
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
helpviewer_keywords:
- COleDispatchException [MFC], m_dwHelpContext
- COleDispatchException [MFC], m_strDescription
- COleDispatchException [MFC], m_strHelpFile
- COleDispatchException [MFC], m_strSource
- COleDispatchException [MFC], m_wCode
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
ms.openlocfilehash: 06f8d8abd8ea337369ceed62a9944e867d355768
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456233"
---
# <a name="coledispatchexception-class"></a>COleDispatchException 类

处理特定于 OLE `IDispatch` 接口的异常，此接口是 OLE 自动化的重要组成部分。

## <a name="syntax"></a>语法

```
class COleDispatchException : public CException
```

## <a name="members"></a>成员

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|错误的帮助上下文。|
|[COleDispatchException::m_strDescription](#m_strdescription)|口头错误说明。|
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|帮助文件以用于`m_dwHelpContext`。|
|[COleDispatchException::m_strSource](#m_strsource)|生成了异常的应用程序。|
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`的特定错误代码。|

## <a name="remarks"></a>备注

像其他异常类派生自`CException`基类，`COleDispatchException`可与 THROW、 THROW_LAST、 TRY、 CATCH、 AND_CATCH 和 END_CATCH 宏。

一般情况下，应调用[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)来创建和引发`COleDispatchException`对象。

有关异常的详细信息，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)并[异常： OLE 异常](../../mfc/exceptions-ole-exceptions.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleDispatchException`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

##  <a name="m_dwhelpcontext"></a>  COleDispatchException::m_dwHelpContext

标识应用程序的帮助中的帮助上下文 (。HLP) 文件。

```
DWORD m_dwHelpContext;
```

### <a name="remarks"></a>备注

此成员函数设置[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)时引发异常。

### <a name="example"></a>示例

  请参阅 [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)的示例。

##  <a name="m_strdescription"></a>  COleDispatchException::m_strDescription

包含一个口头错误说明，如"磁盘已满。"

```
CString m_strDescription;
```

### <a name="remarks"></a>备注

此成员函数设置[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)时引发异常。

### <a name="example"></a>示例

  请参阅 [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)的示例。

##  <a name="m_strhelpfile"></a>  COleDispatchException::m_strHelpFile

框架填充应用程序的帮助文件的名称与此字符串中。

```
CString m_strHelpFile;
```

##  <a name="m_strsource"></a>  COleDispatchException::m_strSource

框架填充生成了异常的应用程序的名称与此字符串中。

```
CString m_strSource;
```

### <a name="example"></a>示例

  请参阅 [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)的示例。

##  <a name="m_wcode"></a>  COleDispatchException::m_wCode

包含特定于应用程序错误代码。

```
WORD m_wCode;
```

### <a name="remarks"></a>备注

此成员函数设置[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)时引发异常。

## <a name="see-also"></a>请参阅

[MFC 示例 CALCDRIV](../../visual-cpp-samples.md)<br/>
[CException 类](../../mfc/reference/cexception-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDispatchDriver 类](../../mfc/reference/coledispatchdriver-class.md)<br/>
[COleException 类](../../mfc/reference/coleexception-class.md)
