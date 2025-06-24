### 新建项目

为了创建一个gradle项目，你首先需要在你的项目文件夹中，创建一个`settings.gradle.kts`文件，用来保存项目文件中的各种设置。

首先需要设置的是这个项目的名字：

```kotlin
rootProject.name = "GradleTutorial"
```

如果你这个时候打开着idea，你可以尝试着使用idea去链接一下这个项目，使用gradle去链接到刚刚所编写的`settings.gradle.kts`
文件，然后idea就会自动开始导入gradle项目，并创建下列文件：

- `gradlew`和`gradlew.bat`： gradle的运行脚本。用于运行gradle脚本，一般来说window用户使用`gradlew.bat`，而linux和macos用户使用
  `gradlew`。虽然在命令的使用上都是直接使用`gradlew <命令>`这个结构。
- `gradle/wrapper`文件夹里面的`gradle-wrapper.properties`以及`gradle-wrapper.jar`
  文件：每个项目所配备的单独gradle本体以及下载的配置文件。由于gradle的api经常性改变，所以官方很建议为每一个项目都分别配备一个gradle本体，这样才能确保每个项目的gradle脚本不会出现问题。

>
如果没有使用魔法的国内同学，很可能会在这一步卡住很久或者报错下载超过时间，解决方案请查看[镜像配置攻略](02-配置国内镜像.md)。

现在你可以尝试在项目根目录使用`./gradlew help`来测试一下，你的gradle项目是否配置成功，出现`BUILD SUCCESSFUL`
字样，则说明以及成功配置好了gradle项目，可以正常使用。

---

### `build.gradle.kts`

`build.gradle.kts`文件是一个项目的构建脚本，如果你需要对这个项目进行个性化定制，基本上你的代码都需要在这里面编写。

如果你仅仅是需要让你的gradle项目成功构建完毕，`build.gradle.kts`文件并不是必须的，但是只要你需要使用到自定义功能，就需要在这个文件里面改动代码。

任务(tasks)，是一种最基础的自定义内容的方式。我们可以通过自定义任务，让gradle了解到我们可以执行什么自定义的操作，并让我们需要执行的时候可以通过调用一个简单的命令就可以进行调用。

现在就让我们创建一个最简单的gradle任务：

```kotlin
tasks.register("hello") {
    doLast {
        println("Hello world!")
    }
}
```

现在，你可以在你的终端界面，执行下列命令：`gradlew hello`

然后你就会看到，你的控制台上面成功打印了`Hello world!`，这表明你的代码成功运行