---
title: Installation - Aspose.TeX for Java
type: docs
weight: 60
url: /java/installation/
---

## Installing Aspose.TeX for Java from Aspose Repository
Aspose hosts all Java APIs on Aspose Repository. You can easily use Aspose.TeX for Java API directly in your Maven Projects with simple configurations.

## Specify Aspose Repository Configuration
First you need to specify Aspose Repository configuration / location in your Maven pom.xml as follows:

```
<repositories>
     <repository>
         <id>snapshots</id>
         <name>repo</name>
         <url>http://repository.aspose.com/repo/</url>
     </repository>
</repositories>
```
## Define Aspose.TeX for Java API Dependency
Then define Aspose.TeX for Java API dependency in your pom.xml as follows:
```
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-tex</artifactId>
        <version>21.4</version>
    </dependency>
</dependencies>
```
After performing above steps, Aspose.TeX for Java dependency will finally be defined in your Maven Project.