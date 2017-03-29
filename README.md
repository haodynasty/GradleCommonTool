# GradleCommonTool
> config only once, create nice code!

- Click Star if you like this plugin, thank you!
- if you have more tools, welcome commit you idea!

# How to use
1. add plugin to app.gradle file
```
apply from: 'https://raw.githubusercontent.com/haodynasty/GradleCommonTool/master/tools.gradle'
...
```
2. using in gradle, like this
```
apply from: 'https://raw.githubusercontent.com/haodynasty/GradleCommonTool/master/tools.gradle'

fir{
  apiToken getLocalProperty("FIR_TOKEN")
  changeLog gitLogFirstCommit()
}

//define apk name
applicationVariants.all { variant ->
    variant.mergedFlavor.versionCode = gitVersionCode()
    variant.mergedFlavor.versionName = gitVersionTag()
    variant.outputs.each { output ->
        output.outputFile = new File(
                 output.outputFile.parent + "/${variant.buildType.name}",
                 "ble-${variant.buildType.name}-${variant.versionName}-${variant.versionCode}-${variant.productFlavors[0].name}-${releaseTime()}.apk".toLowerCase())
    }
}
```

3. Method

- getLocalProperty("key") // get value from local.properties
- localPropertiesFile() //get local.properties file
- releaseTime() //get system time
- gitVersionCode() //get version from git by commit number
- gitVersionTag() //get tag of git(ps: tag is 1.0, commit 2 numbers after tag, the version is 1.0.2)
- gitLogFirstCommit() //get first commit log

# Link
- [organizing_build_logic](https://docs.gradle.org/current/userguide/organizing_build_logic.html)
- [BLOB](http://www.blakequ.com)

