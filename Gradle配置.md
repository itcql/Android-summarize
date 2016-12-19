[TOC]
##打包时自动生成APK文件名称

```

android {

    applicationVariants.all { variant ->
        variant.outputs.each { output ->
            def outputFile = output.outputFile
            def productFlavor = ""
            if (variant.productFlavors[0] == null) {
                productFlavor = "ALL"
            } else {
                productFlavor = variant.productFlavors[0].name.toUpperCase()
            }
            def versionCode = "V" + variant.versionCode
            def currDate = getCurrDate()
            def buildType = variant.buildType.name.toUpperCase()
            def split = "_"
            if (outputFile != null && outputFile.name.endsWith('.apk')) {
                def fileName = "TeamScheduleManager" + split + versionCode + split + productFlavor + split + currDate + split + buildType + ".apk";
                output.outputFile = new File(outputFile.parent, fileName)
            }
        }
}
```