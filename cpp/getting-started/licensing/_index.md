---
title: Licensing - Aspose.TeX for C++
type: docs
weight: 70
url: /cpp/licensing/
description: When you stopped on the licensed version of the Aspose.TeX API solution for C++ here you find out how to apply the license.
---

## **Evaluate Aspose.TeX**
You can easily download Aspose.TeX for C++ product for evaluation purposes. Please refer to the [Aspose.TeX for C++ download page](https://www.nuget.org/packages/Aspose.TeX.Cpp/) to find out the latest version. The evaluation download is same as the purchased download. The evaluation version simply becomes licensed when you add a few lines of code to apply the license.

### **Evaluation Version Limitations**
Evaluation version of Aspose.TeX (without a license specified) provides full product functionality except that only up to four first pages can be obtained in output document. Also, those pages will be stamped with evaluation mode watermark.

If you want to try Aspose.TeX out without evaluation limitations, request a 30-day temporary license. Please refer to [How to get a Temporary License?](https://purchase.aspose.com/temporary-license) for more information.

## **Applying a License**
Once you are happy with your [evaluation]() of Aspose.TeX for C++, buy a license at the Aspose website: [Purchase Portal](http://www.aspose.com/purchase/default.aspx). Make yourself familiar with the different license types available. If you have any questions, [contact the Aspose sales team](http://www.aspose.com/corporate/contact/default.aspx) and they'll be happy to help you.

Every Aspose license carries a one-year subscription for free upgrades to any new versions or fixes that come out during this time. We provide free and unlimited technical support to both licensed and evaluation users.

The license is a plain text XML file that contains details such as the product name, number of licensed developers, subscription expiry date and so on. The file is digitally signed, so do not modify the file: even adding an extra line break to the file invalidates it.
### **When to Apply a License**
Follow these simple rules:

- The license only needs to be set once per application domain.
- You need to set the license before using any other Aspose::TeX classes.
- Calling SetLicense multiple times is not harmful, but wastes processor time.
- If you are developing an application, call SetLicense in the startup code, before using Aspose::TeX classes.
- If you are developing a class library, you can call SetLicense from a static constructor of the class that uses Aspose::TeX. The static constructor executes before an instance of your class is created making sure Aspose::TeX license is properly set.
### **Apply License using File or Stream Object**
Use the [License::SetLicense](https://reference.aspose.com/tex/cpp/class/aspose.te_x.license) method to license the component. The easiest way to set a license is to put the license file in the same folder as the Aspose.TeX.dll and specify the filename, without a path, as shown below.
#### **Loading a License from File**
This code snippet initializes a license stored in a file or in an embedded resource.

{{< gist "aspose-com-gists" "d3eef38ac5b929503e8edee25e0873ce" "Aspose.TeX.Examples-LoadLicenseFromFile.cpp" >}}
#### **Loading a License from a Stream Object**
These code snippets initialize the license from stream.

{{< gist "aspose-com-gists" "d3eef38ac5b929503e8edee25e0873ce" "Aspose.TeX.Examples-LoadLicenseFromStream.cpp" >}}
