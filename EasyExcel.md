---
title: EasyExcel
---

## 基本概念

![image-20230916123533977](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309161235024.png)

![image-20230916123742940](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309161237971.png)

## 快速入门

![image-20230916144026335](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309161440378.png)

![image-20230916164018578](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309161640624.png)

## 进阶操作

![image-20230916164125273](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309161641313.png)

![image-20230916210719250](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309162107352.png)

![image-20230916213253006](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309162132052.png)

![image-20230916213822743](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309162138781.png)

![image-20230916214840301](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309162148347.png)

EasyExcel.read(file.getInputStream(), GoodsExcelDTO.class, new GoodsListener(goodsService)).sheet().headRowNumber(1).doRead(); 这个headRowNumber是什么意思？

在上面提供的代码中，`headRowNumber(1)` 是 EasyExcel 中的一个方法调用，用于指定 Excel 文件中包含表头信息的行号。具体来说，这里的 `headRowNumber(1)` 意味着 Excel 文件的表头信息位于第一行。

在使用 EasyExcel 读取 Excel 文件时，通常会将第一行或某一行作为表头信息，以便正确解析数据并映射到相应的对象模型中。通过指定 `headRowNumber`，你可以告诉 EasyExcel 在哪一行寻找表头信息，以便它能够正确地解析数据。

在你的示例中，`headRowNumber(1)` 表示你的 Excel 文件的表头信息位于第一行，因此 EasyExcel 应该从第一行开始解析数据。如果你的 Excel 文件的表头信息位于不同的行，你可以相应地更改 `headRowNumber` 的参数值以匹配实际情况。