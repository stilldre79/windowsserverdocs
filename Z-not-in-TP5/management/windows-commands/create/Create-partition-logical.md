---
title: Create partition logical
ms.custom: na
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.technology: 
  - techgroup-storage
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1f59b79a-d690-4d0e-ad38-40df5a0ce38e
---
# Create partition logical
Creates a logical partition in an existing extended partition. You can only use this command on master boot record (MBR) disks.

For examples of how this command can be used, see [Examples](#BKMK_examples).

## Syntax

```
create partition logical [size=<n>] [offset=<n>] [align=<n>] [noerr]
```

## Parameters

|Parameter|Description|
|-------------|---------------|
|size=<n>|Specifies the size of the logical partition in megabytes (MB), which must be smaller than the extended partition. If no size is given, the partition continues until there is no more free space in the extended partition.|
|offset=<n>|Specifies the offset in kilobytes (KB), at which the partition is created. The offset rounds up to completely fill whatever cylinder size is used. If no offset is given, then the partition is placed in the first disk extent that is large enough to hold it. The partition is at least as long in bytes as the number specified by **size=<n>**. If you specify a size for the logical partition, it must be smaller than the extended partition.|
|align=<n>|Aligns all volume or partition extents to the closest alignment boundary. Typically used with hardware RAID Logical Unit Number (LUN) arrays to improve performance.  <n> is the number of kilobytes (KB) from the beginning of the disk to the closest alignment boundary.|
|noerr|For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code.|

## Remarks

-   If the **size** and **offset** parameters are not specified, the logical partition is created in the largest disk extent available in the extended partition.

-   After the partition has been created, the focus automatically shifts to the new logical partition.

-   A basic MBR disk must be selected for this operation to succeed. Use the **select disk** command to select a disk and shift the focus to it.

## <a name="BKMK_examples"></a>Examples
To create a logical partition of 1000 megabytes in size, in the extended partition of the selected disk, type:

```
create partition logical size=1000
```

#### Additional references
[Command-Line Syntax Key](../Command-Line-Syntax-Key.md)

[Diskpart \[LH\]](assetId:///26a4a166-95fa-4faf-95bc-2d5345f4a57a)

