[TOC]
##打包时自动生成APK文件名称

```

apply plugin: 'com.android.application'

dependencies {
    compile fileTree(dir: 'libs', include: '*.jar')
    compile('com.dfjl.cld') {
        exclude group: 'xmlpull'
    }
   
}

android {
    compileSdkVersion rootProject.ext.compileSdkVersion
    buildToolsVersion rootProject.ext.buildToolsVersion
    defaultConfig {
        applicationId ""
        minSdkVersion rootProject.ext.minSdkVersion
        targetSdkVersion rootProject.ext.targetSdkVersion
        versionCode 1
        versionName ""
        //dex突破65535限制
        multiDexEnabled true
    }
    signingConfigs {
        debug {
        }
        release {
            storeFile file("keystore")
            storePassword "123"
            keyAlias "123"
            keyPassword "123"
        }
    }

    buildTypes {
        debug {
            //是否开启混淆
            minifyEnabled false
            //是否要开启压缩资源(开启该项需要开启混淆 去除无用的resource文件)
            shrinkResources false
            //在默认版本名称的基础上加后缀
            versionNameSuffix "-debug"
            //是否对APK包执行ZIP对齐优化
            zipAlignEnabled false
            //application后缀(需要跟正式版一块装开启)
            //applicationIdSuffix ".debug"
        }
        release {
            //是否开启混淆
            minifyEnabled false
            //是否要开启压缩资源(开启该项需要开启混淆 去除无用的resource文件)
            shrinkResources false
            //是否对APK包执行ZIP对齐优化
            zipAlignEnabled true
            //使用签名配置
            signingConfig signingConfigs.release
        }
    }

    //渠道名最好大写(不能用小写的all,要不然不能重命名)
    productFlavors {
        cs{

        }
    }

    dexOptions {
        javaMaxHeapSize "2g"
    }

    lintOptions {
        abortOnError false
    }

    compileOptions {
        encoding "UTF-8"
        sourceCompatibility JavaVersion.VERSION_1_7
        targetCompatibility JavaVersion.VERSION_1_7
    }

    sourceSets {
        main {//eclipse转as
            manifest.srcFile 'AndroidManifest.xml'
            jniLibs.srcDirs = ['libs']
            java.srcDirs = ['src']
            resources.srcDirs = ['src']
            aidl.srcDirs = ['src']
            renderscript.srcDirs = ['src']
            res.srcDirs = ['res']
            assets.srcDirs = ['assets']
        }
    }

    packagingOptions {
        exclude 'META-INF/DEPENDENCIES'
        exclude 'META-INF/NOTICE'
        exclude 'META-INF/LICENSE'
        exclude 'META-INF/LICENSE.txt'
        exclude 'META-INF/NOTICE.txt'
    }

    //重命名APK
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
}

```